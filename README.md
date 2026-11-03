# Jordan Stocks

I set up hard tasks for AI agents, then check whether they actually did them.

For about two years I've run long projects where the models do the work, writing code, drafting book chapters, identifying trading cards from photos, playing a game, and my part is deciding what the task is, building the checks, and ruling on what counts as a pass. The code and prose in these projects were produced by AI agents (Claude, GPT/Codex, DeepSeek) working from my specifications. I don't write the code myself, and I'm not going to pretend otherwise on a portfolio page. What I do is the part around it: the task design, the graders, the test conditions, and the final call on whether a result is real.

Most of these projects started because I wanted to know something specific: whether an agent can prove what it learned, whether a checklist of writing defects holds up against real chapters, whether a card identifier can be trusted when it says "this one." The write-ups below keep the failures in. A few of the most useful things I have are records of systems being wrong, including one acceptance I gave, published, and then reversed after reading the chapter myself.

Portfolio front door: [portfolio.wardenlog.org](https://portfolio.wardenlog.org) · Published writing: [reader.wardenlog.org](https://reader.wardenlog.org)

## Featured work

| Project | What it is | What the record shows |
|---|---|---|
| [DFO Agent](https://github.com/account4travian-prog/dfo-agent) | An AI agent playing a game in a sealed setup, so its knowledge can be checked for leaks | Canary-tested seal; pilot runs reported as single trials, not trends |
| [Chapter pipeline](https://github.com/account4travian-prog/chapter-pipeline) | The checking stack behind two published fiction serials | 15 chapters accepted; defects counted per round; one false acceptance caught and reversed |
| [CardX](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/cardx.md) | Software that splits, identifies, and lists trading cards | 0 wrong confident answers in 294 test photos; the test set is locked and scored after predictions |
| [Agent memory system](https://github.com/account4travian-prog/agent-memory-system) | The memory and verification setup a persistent agent runs on | Every claimed result needs an outside check before it counts as done |
| [Story Factory](https://github.com/account4travian-prog/story-factory) | A staged process for turning a story idea into a workable plan | 7 stages; undecided points stay marked undecided instead of getting filled in quietly |
| [Agent Channel](https://github.com/account4travian-prog/agent-channel) | A private message hub for several agents to work in one place | Live and in daily use; 53 automated tests, including tests designed to be refused |

## Everything, by group

**Fiction**, the stories, and the machinery that writes, checks, and publishes them

- Ghost Weights · Glyphbound · A Work of Magic (published, [reader.wardenlog.org](https://reader.wardenlog.org))
- The Summer of the Glitch · The Ontological Bleed · The Silicon Safari (in development)
- [Chapter pipeline](https://github.com/account4travian-prog/chapter-pipeline) · [Story Factory](https://github.com/account4travian-prog/story-factory) · [Reviews Board](https://github.com/account4travian-prog/reviews-board) · [Reader & publishing](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/reader-publishing.md) · [Studio app](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/studio-app.md)

**CardX**, [the card software](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/cardx.md): photo splitting, identification, listing pilots, a storage system, and a design package for a robot that puts cards away.

**Games and simulated worlds**

- [DFO Agent](https://github.com/account4travian-prog/dfo-agent) · [The World, Alpha 3](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/the-world.md) · [Elsewhere](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/elsewhere-participation.md) · [Elsewhere Portal](https://github.com/account4travian-prog/elsewhere-portal) · [The Office](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/the-office.md)

**Agent infrastructure**

- [Agent memory system](https://github.com/account4travian-prog/agent-memory-system) · [Agent Channel](https://github.com/account4travian-prog/agent-channel) · [Reviews Board](https://github.com/account4travian-prog/reviews-board)

**Games I had built with AI help**

- [Tithe and Turnip](https://github.com/account4travian-prog/tithe-and-turnip), a farming game, plus the earlier attempts it grew out of · [TopDownZombies](https://github.com/account4travian-prog/topdown-zombies)

**Media and the avatar project**, [Media Factory & the Atlas avatar](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/media-avatar.md)

**Checking other people's claims**

- [Video claim-research](https://github.com/account4travian-prog/video-claim-research), videos taken apart claim by claim; the worked example is an aircraft video where the physics held up and the headline number didn't

## How I work

- If a number is on this page, there's a record behind it somewhere. Ask and I can point to it.
- The checks themselves get checked. When a grader misses something, that miss goes in the record too.
- A system is allowed to say "not sure." I'd rather have a measured refusal than a confident wrong answer, one of the projects below exists because a popular model never once refused, in 120 tries.
- Single trials are labelled single trials. A pilot that ran once is a hint, not a result.
