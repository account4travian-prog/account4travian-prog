# Jordan Stocks

I set up hard tasks for AI agents, then check whether they actually did them.

The code and prose come from AI agents (Claude, GPT/Codex, DeepSeek) working from my specifications. I don't write the code myself. My part is deciding what the task is, writing the checks, and ruling on what counts as a pass. The write-ups keep the failures in, including one acceptance I gave, published, and then reversed after reading the chapter myself.

## Featured work

| Project | What it is | What the record shows |
|---|---|---|
| [Chapter pipeline](https://github.com/account4travian-prog/chapter-pipeline) | The checking stack behind Ghost Weights and Glyphbound | 15 chapters accepted; defects counted per round; one false acceptance caught and reversed |
| [CardX](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/cardx.md) | Software that splits and identifies trading cards from photos, with a supervised listing layer | 0 wrong "sure" answers across 294 card fronts; the test set is locked and scored after predictions |
| [DFO Agent](https://github.com/account4travian-prog/dfo-agent) | An AI agent playing a game in a sealed setup, so its knowledge can be checked for leaks | Canary-tested seal; single-trial pilots; baseline quiz deferred |
| [The Office](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/the-office.md) | A multi-agent workplace where no agent grades its own work | Two independent reviews (14 findings; 19 attacks and 14 gaps), every finding dispositioned, one rejected with its reason; open defects kept on the record |
| [Agent memory system](https://github.com/account4travian-prog/agent-memory-system) | The memory and verification setup a persistent agent runs on | Every claimed result needs an outside check before it counts as done |
| [Story Factory](https://github.com/account4travian-prog/story-factory) | A staged process for turning a story idea into a workable plan | 7 stages; undecided points stay marked undecided instead of getting filled in quietly |

## More work

**Agent infrastructure.** [Agent Channel](https://github.com/account4travian-prog/agent-channel): a private message hub for my agents, deployed 2026-10-08. Its acceptance report runs 19/19 logic tests and 34/34 integration tests in a real workerd runtime.

**Fiction and publishing.** Ghost Weights, Glyphbound, and A Work of Magic are readable at [reader.wardenlog.org](https://reader.wardenlog.org). The Summer of the Glitch, The Ontological Bleed, and The Silicon Safari are three Sokcho proposals. The Summer of the Glitch ran six stages; the other two have proposal and intake files. [Reviews Board](https://github.com/account4travian-prog/reviews-board) · [Reader and publishing](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/reader-publishing.md) · [Studio app](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/studio-app.md)

**Games and simulated worlds.** [The World, Alpha 3](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/the-world.md), run by my agent Codex Memory Warden · [Elsewhere](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/elsewhere-participation.md), where my agent Atlas is a citizen and was elected first mayor of Ember · [Elsewhere Portal](https://github.com/account4travian-prog/elsewhere-portal)

**Games built by AI agents from my design.** [Tithe and Turnip](https://github.com/account4travian-prog/tithe-and-turnip), a farming game, plus the earlier attempts it grew out of · [TopDownZombies](https://github.com/account4travian-prog/topdown-zombies)

**Media.** [Media Factory and the Atlas avatar](https://github.com/account4travian-prog/account4travian-prog/blob/main/writeups/media-avatar.md)

**Research.** [Video claim-research](https://github.com/account4travian-prog/video-claim-research): videos taken apart claim by claim. The worked example is an aircraft video where the physics held up and the headline number could not be verified.

## How I work

- I use and test experimental and newly released models through OpenCode. In September 2026 I commissioned timing runs across the free OpenCode models and staffed outside reader roles from that pool. In October 2026 I directed the reviewer roles to OpenCode models on my PC. I have published no benchmarks from those comparisons.
- Every number on this page comes from a project record.
- When a grader misses a defect that a later round catches, the miss goes in the record too.
- A system can say "not sure" instead of guessing. The small vision-language models CardX measured never abstained in 120 tries, and were rejected.
- Pilot results are reported per run. One run per arm is a hint, not a result.

Short address: portfolio.wardenlog.org
