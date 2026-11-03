# Jordan Stocks

**I design long-horizon tasks for AI agents: the prompt, the grader, the rubric — then measure where frontier models fail.**

My role in everything below is designer, director, and evaluator. I write the task specifications, contracts, graders, and acceptance rules; AI coding and writing agents (Claude, GPT/Codex, DeepSeek) produce the code and prose under my direction; nothing ships until I verify it against an independent read. That division is deliberate — it is the work itself.

Currently a security officer at CrossWinds Casino (Park City, KS), funding this research myself. Willing to relocate to Mountain View, CA if a relocation package is available.
Portfolio front door: [portfolio.wardenlog.org](https://portfolio.wardenlog.org) · Writing and published work: [reader.wardenlog.org](https://reader.wardenlog.org)

## Featured work

| Project | What it proves | Hard numbers |
|---|---|---|
| [DFO Agent](https://github.com/account4travian-prog/dfo-agent) | Task design + contamination control for an embodied agent | Sealed models, canary-tested information seal, leak rate measured by an independent auditor; memory on/off pilots reported with their n=1 limits |
| [Chapter pipeline](https://github.com/account4travian-prog/chapter-pipeline) | Layered graders for long-form generation | 15 chapters accepted; defect density + escape rate per round; one false acceptance caught by the owner and reversed |
| [CardX](https://github.com/account4travian-prog/cardx) | Grader design + statistical certification for computer vision | 0 wrong "sure" in 294 fronts; Wilson 95% bound target ≈381 clean answers; hash-locked test set, predictions before scoring |
| [Agent memory system](https://github.com/account4travian-prog/agent-memory-system) | Evaluation discipline for a persistent agent | Verified done-conditions, negative-witness tests, effect verification ("did the world change, not did the script run") |
| [Story Factory](https://github.com/account4travian-prog/story-factory) | Task-spec design with gates that can fail | 7 stages, undecided items stay OPEN by rule; real projects run through Stage 6 |
| [Agent Channel](https://github.com/account4travian-prog/agent-channel) | Specified + verified multi-agent infrastructure | Live at agents.wardenlog.org; 53 tests (19 logic + 34 integration), negative-witness table included |

## All projects, by group

**Fiction writing** — the stories and the machinery that writes, reviews, and publishes them
- Ghost Weights · Glyphbound · A Work of Magic (published serial fiction — [reader.wardenlog.org](https://reader.wardenlog.org))
- Summer of the Glitch · The Ontological Bleed · The Silicon Safari (works in progress)
- [Chapter pipeline](https://github.com/account4travian-prog/chapter-pipeline) · [Story Factory](https://github.com/account4travian-prog/story-factory) · [Reviews Board](https://github.com/account4travian-prog/reviews-board) · [Reader & publishing system](writeups/reader-publishing.md) · [WriteProject Studio app](writeups/studio-app.md)

**CardX / Aegis Card Emporium** — computer vision for trading cards: [CardX](https://github.com/account4travian-prog/cardx) (splitter, identifier, listing pilots, storage system, robotic put-away design package)

**AI in games & simulations**
- [DFO Agent](https://github.com/account4travian-prog/dfo-agent) · [The World — Alpha 3, Genesis Island](writeups/the-world.md) · [Elsewhere participation](writeups/elsewhere-participation.md) · [Elsewhere Portal](https://github.com/account4travian-prog/elsewhere-portal) · [The Office](writeups/the-office.md)

**AI agent infrastructure, memory & operations**
- [Agent memory system](https://github.com/account4travian-prog/agent-memory-system) · [Agent Channel](https://github.com/account4travian-prog/agent-channel) · [Reviews Board](https://github.com/account4travian-prog/reviews-board)

**Game development (AI-assisted)**
- [Tithe and Turnip](https://github.com/account4travian-prog/tithe-and-turnip) — the whole farm-game line, including the harness optimizer · [TopDownZombies](https://github.com/account4travian-prog/topdown-zombies)

**Media, brand & avatar** — [Media Factory & the Atlas avatar programme](writeups/media-avatar.md) · Memory Warden brand

**Research, analysis & verification systems**
- [Video claim-research system](https://github.com/account4travian-prog/video-claim-research) — claim-by-claim verification; case study: an aircraft-Doppler geolocation video (physics supported, headline result unverified)

## How I work
- **No claim without a source.** Every number above traces to a record.
- **Graders get graded.** Escape rates, refuted-checks lists, and reversed acceptances are kept, not hidden.
- **Abstention is a feature.** Systems I design may refuse to answer — a measured "not sure" beats a confident wrong answer.
- **Negative results are results.** Single-run pilots say so; failed designs stay in the record with the reason.
