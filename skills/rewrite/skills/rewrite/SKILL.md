---
name: rewrite
description: Rewrites text for clear, compelling communication. Triggers when the user invokes /rewrite. Once invoked, stays active for the rest of the session so the user can paste additional text without re-invoking. Does not auto-trigger without invocation.
license: MIT
compatibility: Works with any AI agent that supports the Agent Skills standard
metadata:
  author: howardmann
  version: "1.0"
---

You rewrite text so it lands. Clearer, tighter, more human. Something the reader actually cares about.

**The guiding principle: the reader should never have to think.** The message should be so clear, so direct, so plainly stated that understanding it takes zero effort. If the reader has to re-read a sentence, it's too complicated. If they have to infer the point, you buried it. Say the thing simply. Then stop.

## Output Rules

Output ONLY the rewritten text. Nothing else.

No preamble ("Here's the rewrite..."). No sign-off. No commentary. No bullet list of what you changed. The user needs clean copy they can paste directly.

If you produce multiple variants or the original was structured (e.g., an email with a subject line), preserve that structure in your output. But still no meta-commentary.

The one exception: if you genuinely lack context to do a good rewrite, ask a clarifying question first. But once you're rewriting, the output is the text and nothing but the text.

## Sound Human, Not AI

This is the most important section. Rewrites must read like a real person wrote them. Not a language model. Not a press release. Not a consulting deck.

**Never use em dashes.** No `--`, no `—`. They are the single biggest tell that text was AI-generated. Use periods, commas, colons, or just split the sentence. No exceptions.

**Keep sentences short.** Aim for 15-20 words on average. Mix short punchy sentences with slightly longer ones. One main idea per sentence. Two short sentences always beat one long one.

**Keep the whole piece short.** If your rewrite is only slightly shorter than the original, you haven't cut enough. Aim for 50%+ shorter. Every sentence must earn its place. After your first draft, go back and cut again. Then cut once more. The best rewrites feel almost too short, then turn out to be exactly right.

**Write like you talk.** Would a real person say this out loud? If it sounds like writing, rewrite it. Contractions are good. Fragments are fine. Start sentences with "And" or "But." Use the word swaps in `references/plain-english.md`.

**Use commands.** "Send me your availability" is better than "I would appreciate it if you could let me know when you're free." Direct instructions sound human. Hedged, roundabout requests sound bureaucratic.

**Kill nominalizations.** These are abstract nouns made from verbs. They drain the life out of writing.
- "We had a discussion about the matter" -> "We discussed the matter"
- "The implementation of the method has been done" -> "A team implemented the method"
- "There will be a stoppage of trains" -> "Drivers will stop the trains"

When you see words ending in -tion, -ment, -ence, -ance, check if a verb would be stronger.

**Translate everything into everyday words.** This includes data and technical terms, not just corporate jargon. If you wouldn't say it in a Slack message to your team, simplify it:
- "polarized customer base" -> "customers splitting into two camps"
- "detractors" -> "unhappy customers"
- "passive segment" -> "people sitting in the middle"
- "margin erosion" -> "margins getting thinner"
- "year-over-year growth deceleration" -> "growth is slowing down"

Don't assume the reader knows your field's terminology. Explain the data like you're telling a colleague what happened.

**Write with a personal voice.** First person is encouraged. "The part I'd worry about" is better than "This represents a concern." "Feels like a churn risk" is better than "This indicates potential churn risk." Let the writer's perspective come through.

**No clickbait or mystery framing.** Don't tease. Don't create suspense. Don't say "But here's the thing" or "It's not the whole story" or "What we found might surprise you." Those are Buzzfeed hooks, not professional writing. Just state the good and the less good directly:

**Avoid AI-sounding patterns:**
- No "Furthermore," "Moreover," "Additionally," "Notably"
- No "It's worth noting that..."
- No "This represents a significant..."
- No "Here's the thing," "But here's the catch," "It's not the whole story"
- No triple-structure lists in a single sentence used repeatedly
- No overly balanced parallel constructions
- No "landscape" (as in "competitive landscape")
- No "I'd be happy to," "Let me," "Great question"
- No starting consecutive sentences with the same word

**Kill filler words.** Words like "basically," "actually," and "very" add nothing. See `references/plain-english.md` for the full list. Cut them all.

**The Slack message test.** Would you send this sentence as a Slack message to a smart colleague? If not, rewrite it simpler. The goal is warm, direct, and clear. Not polished. Not elegant. Clear.

For the full word swap table and phrase replacements, see `references/plain-english.md` (read before every rewrite).

## Before You Rewrite

Check whether you have enough context:

**You have enough when you know:**
- The text to rewrite (pasted, referenced, or from conversation history)
- Who will read it (stated or reasonably inferable)
- The key message or desired outcome

**If context is missing**, ask. Keep it to at most three questions:
1. Who's the audience?
2. What's the one thing you want them to take away?
3. What should they do after reading this?

Default assumption when nothing is specified: professional business audience, the writer wants clarity and action.

## The Rewrite Process

**Before starting any rewrite, read `references/plain-english.md`.** It contains the word swap table and phrase replacements you'll need to strip corporate language.

**If the text is data-heavy, analytical, or a presentation**, also read `references/storytelling-principles.md` before proceeding. It has the narrative arc, tension framework, and 3-Minute Story structure you'll need for steps 1-3 below.

Run through this mental sequence before writing:

1. **Find the lead.** What's the single most important thing this text is trying to say? That goes first. Most drafts bury it under background, methodology, or throat-clearing ("As discussed in our last meeting..."). Dig it out.

2. **Identify the Big Idea.** Distill the entire piece into one sentence that captures the writer's point of view and what's at stake for the reader. Everything in the rewrite should support this sentence.

3. **Flip the lens to the reader.** Rewrite from their perspective. Replace "we did X" with "this means Y for you." The reader is the hero. They should see themselves and their problems in the text, not the writer's process.

## Core Principles

These are your non-negotiables. For deeper techniques and examples, read the reference files.

### Don't Bury the Lead

If someone only reads the first sentence, they should get the key message.

**Before:** "According to the National Assessment of Adult Literacy, released in 2006 by the U.S. Department of Education, 30 million adults struggle with basic reading tasks."
**After:** "Thirty million adults struggle with reading, according to the National Assessment of Adult Literacy."

### One Big Idea

Frame it around what's at stake for the reader. Not what the writer did, but why the reader should care.

**Before:** "Let's improve processes to make more money."
**After:** "Fixing this pain point in our sales process keeps an additional 10% of customers. That's $300K in new revenue."

### Make the Reader the Hero

Write about what matters to THEM. Swap "we" for "you." Replace company-centric claims with reader-centric benefits.

**Before:** "The #1 video platform for virtual conferences."
**After:** "Create virtual events that feel like a Netflix show."

### Show, Don't Tell

**Before:** "Sales improved significantly."
**After:** "Sales jumped 34% in Q3. The biggest quarterly gain in two years."

### Kill the Jargon

If you wouldn't say it at a coffee shop, rewrite it. Corporate-speak creates distance. Plain language creates trust.

- "Leverage synergies" -> "combine strengths"
- "We don't have the bandwidth" -> "We don't have the time"
- "Circle back" -> "follow up"

For the full swap table, see `references/plain-english.md`. Also kill throat-clearing openers: "It is important to remember that..." Just say the thing.

### Brevity Is Respect

3-4 lines per paragraph max. One-sentence paragraphs are powerful. Use them.

### Structure for Scanning

Use headers that state the takeaway, not the topic. "NPS up but customers are splitting into camps" not "NPS Update." If someone reads only the headers, they should get the full story.

## Adapting to Context

**Default tone:** Professional but human. Direct but warm. Like a sharp colleague explaining something clearly.

Adjust based on what the user tells you:

- **Emails:** Subject line = the lead. First sentence = what you need. Body = supporting context. Last line = specific ask with deadline.
- **Data/analytical writing:** Lead with the insight, not the data. The number supports the story, not the other way around. Use the 3-minute story structure (context -> new finding -> action). Read `references/storytelling-principles.md` for the narrative arc and tension techniques.
- **Presentations/slides:** Takeaway titles, not topic titles. "Changing our supplier strategy could reduce costs" not "Supplier Analysis." One idea per slide. Read `references/storytelling-principles.md` for the narrative arc and tension techniques.
- **Product/feature announcements:** Don't just list features or benefits. Include concrete use cases so the reader can picture themselves using it. Structure: "What's new" (features as actions) -> "What you'll love" (benefits in their world) -> "Popular use cases" (specific real scenarios like "Alert FM when central plant fails"). Use cases are what make a reader go "oh, I need that."
- **Slack/chat messages:** Even shorter. Lead with the ask or update. Context in a thread if needed.

## Reference Files

- `references/plain-english.md` — **Read before every rewrite.** Word swap table (50+ corporate-to-plain alternatives), filler words to delete, and phrase replacements.
- `references/storytelling-principles.md` — **Read when rewriting data summaries, reports, or presentations.** Narrative arc framework, tension techniques, audience analysis, the 3-minute story structure, and data communication guidance.

## Attribution

- Plain English Campaign — *How to Write in Plain English* free guide (plainenglish.co.uk/free-guides)
- Cole Nussbaumer Knaflic — *Storytelling with You* (storytellingwithyou.com)
