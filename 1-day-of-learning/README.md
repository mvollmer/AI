# DAY OF LEARNING: AI

I am interested in the "mathematical" side of computers, data
structures and algorithms, and also in the "egineering" and "art"
parts of programming, managing complexity and inventing tasteful
abstractions in the form of APIs and programming languages.

I am not interested in AI as a technology, it looks like a bunch of
ad-hoc computations on large amounts of data. I think it's more the
amount of data that makes AI work, not the algorithms. It sure is
fascinating and impressive, as a toy, but I am happy to stay out of
the details of how it actually works, and I am patiently waiting for
society to figure out the impacts.

Moreover, I don't feel like using AI for the things that I am genuinly
interested in. I don't want that the AI writes programs for me and
then I go looking for the mistakes in them, with the hope that this
saves time or improves quality. That would be dreadful and take the
fun and motivation out of programming. I _want_ to write code.

I feel that AI is good for ["vibe coding"](https://x.com/karpathy/status/1886192184808149383),
where you don't even look at the code that it produces, only at what
happens when you run it.  Professionally, I don't want to be caught
vibe coding on the job. I feel that would be reckless and
irresponsible.

But there are important things about my job that I am not that
interested in. Maybe AI can help me there:

 - Writing weekly and quarterly reports about what I have done.

 - Digging through Testing Farm links to find the actual test
   failures.

 - Digging through package repositores to figure out which version of
   a package is in which RHEL release.

 - Finding out lifecycle dates for RHEL releases.

In general, my attitude right now is: Please bring AI to me, I will
not be offended. But I don't feel like pulling AI closer to me by
myself.

Except for this Day Of Learning.

## Previous experience

I have taken part in the IBM effort with their open AI thing (forgot
the name). I could run some model on my old laptop, and I got it to
tell me a Moomin story, slowly.  It didn't have any dialog in it, so I
asked the AI thing to tell the story again with dialog, which it did
flawlessly. I was impressed.

Then I asked about my University professor by name (which is the
father of a slightly famous German footballer, which makes me
personally a world champion!), and the AI thing hallucinated wildly.
I wasn't so impressed anymore.

Reflecting more, I realized I am more impressed by the ability of the
AI thing to "understand" the prompt, than I was by the output.

From that I concluded that AI is useful for creating ("generating")
new fictional things, which can be judged on their own for their
usefulness. A story about Moomins can not be wrong, but it can be good
or bad.

But when AI is asked for facts, the answer is just as likely right as
it is wrong.  Wikipedia can be wrong, sometimes, but AI must be
assumed to be wrong always, and the correctness of its output must be
proven independently.

Recently, we enabled Sourcery.Ai in our Github repositories. It will
review code changes and suggest improvements. Again, I was impressed
by the ability to "understand" what's going on, and how it generates
suggestions that look like reasonable refactorings.

But ultimately it lacked value. Most suggestions were about writing
things in a different style. If that would be proposed by a human, I
would probably take the suggestion instead of argueing about it. I
know the team and trust them only bring up things that they feel
strongly about. But coming from AI? Unwelcome noise.

I still have the feeling that if we would make more obvious mistakes,
Sourcery.Ai would be able to find them, maybe. But it doesn't seem to
be able to contribute on a useful level in our team.

## Let's get into it more

I have only picked up a couple of product names so far but never used
them: ChatGPT, Claude, Copilot, Cursor, Ollama. Let's learn more about
them.

### ChatGPT

 - Googled "chatgpt", landed on chatgpt.com
 - "Ask anything", okay, "What have I done in the last quarter"
 - [Transcript](./chatgpt.md)

 => Not useful, or I had naive expectations.

Can't automate information retrieval, halluzinates freely while
summarizing.  Occasional glimpses of greatness when it uses highly
polished Corporate Speak to make my commit messages sound bombastic,
but I can't use that kind of language in my reports without feeling
like a fraud.

### Claude

 - Goggled "claude", landed on "https://chat.chatbotapp.ai"
 - "Type a message", okay, "I need to summarize my contributions in the last quarter."
 - "Continue with Google", my github email.
 - "Unlock Claude with Pro", no thanks.
 - Ah, this doesn't do anything without money! Fair enough, but not today.
 - Checked the search results again, went to "https://claude.ai"
 - Logged in "With Google", staid on Free Plan.
 - [Transcript](./claude.md)

 => Much better, but I had learned something from ChatGPT already and
    tempered my expectations.

Claude was clear upfront that it can't access GitHub. ChatGPT
tried but probably failed more than it succeeded, without being
frank about it.

This time I used the AI to help me learn how to build my own
automation for a task, instead of trying to get the AI to execute
that mechanical task.  That's a valuable insight for me: If
something is a mechanical task that looks like it can be
automated, don't try to teach the AI to do it. They'll screw it up
eventually. Instead, use the AI to learn how to implement that
automation yourself.

Claude was kinda competent in the beginning but quickly reached
its limits with how to use the "gh" tool.  Maybe with more
iteration and more patience we would have figured it out together,
but I ran out of free messages.

It was able to give initial examples of how to use gh and start
experimenting. I had probably already reached the point where it
is more useful to start reading the actual docs than continuing to
ask Claude about the finer points.

Summarizing with Claude went well, but as expected, it replaces
precision with boasting when summarizing, and I am not looking for
that in my quarterly reports.

### Github Copilot

 - Went to "https://github.com/copilot"
 - Was eligible, yay!
 - Enabled and allowed everything. Yolo!
 - [Transcript](./copilot.md)

 => Went quite well (or I had even lower expectations), but still
    don't think I will use it as a tool. Just can't rely on it. (See
    above re automating tasks.)

I was again trying to get a quarterly report out of it, and
Copilot could properly access my Github data for that. Asking for
a "summary" produces a list but asking for "highlights" produces
something more like a summary.

The choice of models confuses me.

I asked a Rust question that I had on my mind, but didn't learn
anything from it. Probably because I am not prepared enough.

## Deep breath

But, boy, I am starting to get burned out on talking to AI already.
There is a lot of uncertainty of whether or not you'll get a useful
reply and where the conversation is going and when do you hit the
point where the AI just goes off the rails and starts talking
bullshit.

After a couple hours of this, the feeling creeps in that this is just
wasting time and I should just get down and do things the old
fashioned way. Reading documentation, googling for some tutorials,
etc.  I would still need to filter out the bullshit that humans put on
the web, but I feel I am better prepared for that.  Filtering out AI
bullshit seems to be a different skill.

## Let's reflect

So. I have learned about Github search (by correcting the mistakes
that AI has made) and I learned that I can use it to maybe save 5
minutes when preparing quarterly reports.

The AIs have giving good hints at how to go about solving certain
tasks, and that is often all that is needed to set you on the road to
success, even if the AI can't follow you all the way.

I will consider asking Github Copilot instead of Google the next time
I need to look something up, or am looking for some ideas of how
people do certain things. It's a better Google because it keeps
context.

In any case, I feel way more competent in using AI than yesterday.  I
have used it already to learn more about Konflux.  And I have reached
the limits of Copilot on that topic already, I think.  It has giving
me a raw Tekton pipeline instead of the Konflux version, probably,
maybe, while pretending otherwise.

I am left with a feeling of dread... Did I actually learn something,
or have I been listening to a madman spouting bullshit the whole time?

Still, I can see the next Days Of Learning starting out with a Copilot
session, if only to let the AI give me some claim about the technology
that I want to learn about, and then I go and try to prove or disprove
that claim and thereby do the actual learning.
