This greybeard was gently pushed into exploring AI at least a little
bit, and I am actually thankful for that.

First I was asked to do "something with AI, but don't waste time".

[1 - Day of Learning](./1-day-of-learning/)

After this I still had the impression that interacting with AI for
serious stuff is going to be frustrating.

Then I was asked to "use AI at least weekly", and I started looking
for the tools offered and paid for by my company, not just random free
chat bots on the internet.

[2 - Vibing with Cursor](./2-vibing-with-cursor)

This changed my opinion about whether interacting with AI is painful:
It's not, it is mostly fun.

But while the level of "understanding" on part of the AI made for
fluent and pleasant interaction, the results were still underwhelming
and I am not sure if the money and resources were well spent.  I am
seriously thinking I might be cheaper for the company and better for
the environment than AI! And AI is only going to get more expensive
and wasteful.

Still, one evening I lay on the couch and prompted a real pull request
out of Cursor that got merged and released for real:

[3 - Real code](https://github.com/cockpit-project/cockpit-machines/pull/2224)

The bug that prompted this pull request was found by humans. The
research for how to fix it was done by humans but could have been done
by AI. The refactoring and fixing was done by a human plus AI team but
could have been done by a single human in the same amount of time, but
maybe not while laying on a couch with a tired brain after a day of
work.

Just to be clear: I consider this pull request near trivial, it's not
an example of "ohmygert AI is soo amazing you guys".

I don't care for the Cursor IDE, and was only using the chat window in
it.  Code review etc was done in my standard editor.  I have access to
Claude Code on the command line now, which I think will fit my
"workflow" better, so I will try that next.

I will consider using AI for refactory code changes like above, but
not yet for generating significant pieces (a whole function or more)
of new code.

[4 - Claude](https://github.com/cockpit-project/cockpit-machines/blob/e297af6b91207c90a3e72b0b54af8fc99183e15c/test/files/headless-vnc-client.py)

So, Claude.  It's in the terminal and just the chat, and that works
better for me than the biggish Cursor IDE GUI thing. Otherwise it
feels exactly the same, probably because Cursor is using the Claude
models.

I asked it to make me a truly headless VNC client that we can run in
our test environment. I knew it's possible with some Python modules,
but Claude did it by implementing the raw VNC protocol from
scratch. (Only for the initial handshake, which is all we need.)

This was very useful.  I couldn't get it to add working support for
passwords, however. I think the DES implementation that it added was
flawed.

I didn't let Claude write the tests, which it was "eager" to
do. Claude's tests turned out to be very verbose and looked like they
need significant debugging until they would actually work.

5 - Claude?

The headless VNC client did not pass code review and I didn't feel
like actually engaging with it to make it pass. We decided to use the
real VNC viewer in Cockpit to make non-shared connections. This
prompted a hunt and eventual fix for a long-standing non-trivial bug
in our web server. That's a win.

6 - Claude?!

I decided I wanted a LRU cache in cockpit-machines, but felt a mental
block to get started on that: writing one from scratch needs proper
attention and decisions about how to balance complexity and
performance etc, and I felt I should spend my energy elsewhere. So I
let Claude solve this.

The level of "understanding" was enormously impressive. I had earlier
left this comment for myself:

    // TODO
    // - Keep only N most recently used ones.
    // - Include connectionName in key.

and the prompt was just

> The ConsoleCardStates class has TODO items. Complete them.

Claude did that effortlessly, for $0.30.  However, the code for the
LRU cache was wrong.  It generated this:

      export class ConsoleCardStates {
          states = {};
          accessTimes = {};
          maxStates = 10;

          get(vm) {
              const key = `${vm.connectionName}:${vm.id}`;

              if (!this.states[key]) {
                  this.states[key] = new ConsoleCardState();
                  this._cleanupOldStates();
              }

              this.accessTimes[key] = Date.now();
              return this.states[key];
          }

          _cleanupOldStates() {
              const keys = Object.keys(this.states);
              if (keys.length > this.maxStates) {
                  const sortedKeys = keys.sort((a, b) => (this.accessTimes[a] || 0) - (this.accessTimes[b] || 0));
                  const keysToRemove = sortedKeys.slice(0, keys.length - this.maxStates);

                  keysToRemove.forEach(key => {
                      this.states[key].close();
                      delete this.states[key];
                      delete this.accessTimes[key];
                  });
              }
          }
       }

It has two bugs: The resolution of `accessTimes` is only seconds, and
more significantly, `_cleanupOldStates` is called after adding a new
element but before assigning the `accessTime` for this element. This
will result in the new element being removed again immediately.

I could probably have stayed engaged with Claude to test and fix this,
but I didn't and had to return to this later and fixed it up myself
when testing this manually.

So Claude got me out of my mental block, but not much more. It might
have set me on the wrong path, maybe there is a proper LRU cache
somewhere on npm.org, but I'll never know.

I should not expect Claude to provide tested and working code from
known good sources. The first version must be assumed to be broken and
I need to iterate and let Claude see test results. But can I let it
write the tests?

7 - Back at it

[ Time passes ... ]

I felt less external pressure to spend time on AI, so I did less with
AI for a couple of months and enjoyed the kind of "trad coding" that I
like.  I made a framework for implementing dialogs and a new file
chooser dialog as a "functional mockup", for example.

But now it's time to get back into AI and the plan is to learn how
good it is at porting existing dialogs over to the new framework, and
how much it can help with turning the functional mockup into a
production component.

As preparation, I'll tackle two points: Sandboxing of the AI tools
(finally!), and integration with the Patternfly MCP.

7.1 - Sandboxing

I quickly read a company internal thread about AI sandboxing and there
seem to be a lot of personal projects involving all the latest
container tech, in various stages of readiness.  I am certain good
stuff is happening and I am happy for people to be excited, but I
don't want to get involved. My company has guidelines for how to use
AI, but sandboxing is not included yet. Once it is, I'll happily
follow those.

But for now, I modified my existing development setup a bit: I used to
mount my whole home directory read/write into a long lived development
and test VM, but now I only mount the "work/" subdirectory.  Then I
installed and configured Claude for a account in that VM.  I'll
exclusively use that account for running claude.

This should hide all my delicious credentials from Claude.  It will
not be able to push to github in my name, for example.

This is good enough for me.

With that, I let Claude [port a dialog over to the new
framework](https://github.com/cockpit-project/cockpit/pull/23358).
That went quite well, probably because there was already extensive
example code for the framework (and Claude found that all by itself,
even). Also, refactorings like this are essentialy pattern matching
and replacing, which AI should be good at. But it also figured out the
patterns, which is the real timesaver.

There were mistakes of course, and if I had done this by hand it would
have been only slightly slower I guess, and I would have probably
found more opportunities for improvement. But Claude needed very
little hand holding and I could do other stuff on the side. So that's
a win.

7.2 - Patternfly MCP

I got the hint that Patternfly has a "MCP" server and I have never
actually used one, so let's configure it.

And that was very easy and I told Claude to "Check all uses of
Patternfly components for correctness according to patternfly
documentation." in the cockpit-machines project and it came back with
only two issues, [which it was also able to fix](https://github.com/cockpit-project/cockpit-machines/pull/2669).

Ok, now I know how to use MCP servers.

(A few days ago I thought that "Agentic AI" and "MCP" are the same
thing! Can you imagine?)
