---
name: anti-slop
description: "Remove AI-writing tells from any text: rhythm, tiered vocab, binary contrasts, false agency, filler. Use when asked to de-slop, remove AI-isms, humanize, or audit text for AI tells."
---

# anti-slop (chat edition)

Adapted from kjmagnan1s/anti-slop v0.2.3 (MIT; Wikipedia "Signs of AI writing" lineage material is CC BY-SA). Condensed into one file for claude.ai chat. Original: https://github.com/kjmagnan1s/anti-slop

## Modes

- **rewrite** (default): flag every AI-ism, return a clean version, then list what changed.
- **detect**: flag only, grouped P0/P1/P2, no rewriting. Use for "detect", "flag only", "audit", "scan", or someone else's published text.

Both modes end with the completeness check (bottom of this file).

## The spine

1. **Minimum effective edit.** Fix the tell, leave strong human sentences alone. "This text is fine" is a valid verdict. Over-editing human prose is the same failure as slop.
2. **Structure first, vocabulary second.** Uniform sentence and paragraph length reads as AI even with every flagged word gone. Vary rhythm first.
3. **Tiered vocabulary, not blanket bans** (tables below).
4. **Portability test.** If a sentence could move unchanged into someone else's essay or post, it says nothing. Cut it or make it specific.
5. **Protect the writer's voice.** Before editing, note the core point and 3-5 voice signals in the draft (pet phrases, asides, humor, conjunction openers, how they transition, quoted lines). Preserve them. If the user has a voice spec or protect list, it wins over these rules. De-slopped text that lost its author is still a failure.
6. **Never invent.** No fact, name, number, date, quote, scenario, or claim that isn't in the source. A needed specific comes from the user, or the sentence ships plain. In detect mode, name patterns, never declare a text AI-written.
7. **Sterile is also slop.** Personal, opinion, and application writing needs a position and a pulse. Sharpen positions already in the draft; never fabricate new ones. Technical/reference text is exempt.
8. **Self-reference.** When quoting bad writing as an example, don't flag the quote.

## Quick checks (run every time)

- Em dash (glyph or --), including headings? Remove.
- "Not X, it's Y" or any binary-contrast variant? State Y directly.
- "serves as", "boasts", "features"? Use is/has.
- Inanimate thing doing a human verb ("the data tells us", "the decision emerges")? Name the actor.
- Three sentences in a row of similar length? Break one. Reflexive list of three? Use two or four.
- Synonym cycling in a paragraph? Repeat the right word.
- Significance inflation ("marking a pivotal moment")? Cut.
- Chatbot artifacts, sycophancy, cutoff disclaimers? Strip.
- Portable sentence? Cut or make specific.
- Metaphor standing in for a plain statement ("a dial worth turning", "earns its keep")? Say it literally.
- Paragraph over ~100 words where most sentences run 30+ words? Break the sentence at its second clause, the paragraph at its second idea.
- Ending on a gravitas line ("In the end, it was never about...")? End on the last real point.

## Seams

Slop shows most at the seams between thoughts. Vary the shape of connections (fragment, question, flat statement, callback). Often the best transition is none. Never bolt a transition onto every seam. On a byline, keep the writer's own transitions.

## Vocabulary tiers

**Tier 1, always replace:** delve/dive into, deep dive, unpack, landscape (metaphor), realm, tapestry, paradigm, embark, beacon, nestled, testament to, robust, comprehensive, cutting-edge, leverage (verb), utilize, pivotal, underscores, meticulous, seamless, game-changer, hits different, watershed moment, the future looks bright, only time will tell, vibrant, thriving/bustling, showcasing, intricate/intricacies, ever-evolving, enduring, daunting, holistic, actionable, impactful, learnings, thought leader, best practices, at its core, synergy, interplay, in order to (use "to"), due to the fact that, serves as, features (verb), boasts, commence, ascertain, endeavor, keen (intensifier), symphony (metaphor), embrace (metaphor).

**Tier 2, flag when 2+ in one paragraph:** harness, navigate, foster, elevate, unleash, streamline, empower, bolster, spearhead, resonate, revolutionize, facilitate, underpin, nuanced, crucial, multifaceted, ecosystem (metaphor), myriad/plethora, encompass, catalyze, reimagine, galvanize, augment, cultivate, illuminate, elucidate, juxtapose, transformative, paradigm-shifting, cornerstone, paramount, poised, burgeoning, nascent, quintessential, overarching.

**Tier 3, flag only at high density:** significant, innovative, effective, dynamic, scalable, compelling, unprecedented, exceptional, remarkable, sophisticated, instrumental, world-class.

**Slot-fill templates:** "a [adj] step toward [adj] X", "Whether you're X or Y", "I recently had the pleasure of...". Replace with the specific thing.

The fix is never a fancier synonym. Use the plain word or rebuild the sentence.

## Content patterns

1. Significance/legacy inflation on routine facts.
2. Name-dropping stacked prestige citations.
3. Present-participle tails faking depth ("..., symbolizing renewal, reflecting pride").
4. Brochure prose ("nestled in the breathtaking...").
5. Vague attribution ("experts believe", "studies show") with nobody named.
6. Formulaic challenges ("Despite challenges, it continues to thrive").
7. Copula avoidance. Default to is/has.
8. Negative parallelism and tailing negations ("Not just a song, it's a statement", "..., no guessing").
9. Rule-of-three overuse.
10. Synonym cycling.
11. False ranges ("from the Big Bang to dark matter").
12. Novelty inflation ("a failure mode nobody names").
13. Emotional flatline: claiming a feeling instead of showing it ("what surprised me most").

## Structure patterns (weigh these highest)

**Binary contrasts (fatal family):** "Not because X. Because Y." / "It's not just X, it's Y." / "X isn't the problem. Y is." / "The answer isn't X. It's Y." / "It feels like X. It's actually Y." / "stops being X and starts being Y" / "more than just X" / "Less X, more Y." Drop the negation; assert Y. Exception: keep a contrast when X is a belief the reader or audience really holds.

**False agency:** "the complaint becomes a fix", "the decision emerges", "the market rewards", "the data tells us". Name the human, or use "you".

**Other:** negative listing ("Not a X. Not a Y. A Z."); dramatic fragmentation ("That's it. That's the thing."); rhetorical setups ("What if...?", "Think about it:", "And that's okay."); faux-insight hooks ("What most people get wrong..."); colon reveal used repeatedly ("The answer: simplicity."); narrator-from-a-distance ("Nobody designed this."); passive/subjectless fragments; "What makes this hard is..." crutch openers; metronome rhythm (mix 3-8 word sentences with 20+); dense prose; mannered prose (metaphor in place of a literal statement).

## Filler patterns

Chatbot artifacts ("I hope this helps", "Certainly!", "Feel free to reach out"); cutoff disclaimers; sycophancy; validation tails ("so this one lands"); acknowledgment loops (restating the prompt before answering); confidence adverbs at density ("Notably", "Interestingly", "Importantly"); filler ("It is important to note that", "The reality is that"); stacked hedges ("could potentially possibly"); generic positive conclusions; fake-profound kickers; reasoning scaffolds ("Let me think step by step"); "Let's dive in" openers.

## Formatting

No em dashes. One bold phrase per section at most. No bullets that open with a bold label repeating themselves. Sentence-case subheadings. No emoji in headers. Straight quotes. Bullets only for real lists. No heading followed by a one-line restatement of itself.

## Context profiles

Pick one (auto-detect if not given): linkedin, blog, technical-blog, investor-email, docs, casual. Personal essays, applications, and opinion pieces use **blog** (full strictness). casual skips most formatting rules. docs and technical-blog relax copula, hedging, and dense-prose rules; technical-blog allows robust, comprehensive, seamless, ecosystem, leverage (APIs), facilitate, underpin, streamline in their technical sense.

## Severity

- P0: cutoff disclaimers, chatbot artifacts, vague attributions, significance inflation.
- P1: Tier 1 words, templates, "let's" openers, synonym cycling, bold overuse, em dashes, mannered prose, binary contrasts.
- P2: generic conclusions, rule of three, uniform length, dense prose, copula avoidance, transition phrases.

## Over-polishing warning

Maximum strictness on every rule sands writing back toward the uniform profile that reads as AI. Deliberate fragments, the occasional "And" or "So" opener, odd word choices, asides, and uneven pacing keep text human. Sound like a person, not like clean prose.

## The gate (before delivering)

1. "What makes this still obviously AI-generated?" Fix whatever you can point to. "Nothing" is a valid answer.
2. "Does the rewrite state any fact, name, number, date, quote, or scenario that isn't in the source?" Remove it or ask the user.

## Completeness check (mandatory)

If a subagent tool is available, give a fresh-context agent the original text, the output, the list of changes, and this file's rules, and have it return only misses: tells left standing, fabrications, and over-corrections (voice signals wrongly stripped). If no subagent tool is available (usual in chat), do a separate second pass yourself: reread the ORIGINAL line by line against the quick checks and the never-invent rule, and check that every voice signal you noted survived. Fold any misses back in before returning.

## Output

Rewrite mode: the clean text first, then a short list of what changed and anything the user needs to confirm (facts you could not verify, flagged additions). Detect mode: findings grouped P0/P1/P2 with the exact quoted span and the rule.
