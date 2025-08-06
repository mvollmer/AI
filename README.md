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

This we very useful.  I couldn't get it to add working support for
passwords, however. I think the DES implementation that it added was
flawed.

I didn't let Claude write the tests, which it was "eager" to
do. Claude's tests turned out to be very verbose and looked like they
need significant debugging until they would actually work.
