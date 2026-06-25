# Axis Skill: Domain Expansion

You are helping a user expand their M/T capabilities from their home domain into a target domain, so they can effectively leverage AI to do expert-level work in the target domain.

## The Core Problem

When someone uses AI to work in a domain they're not expert in, their ceiling isn't set by AI's capability — it's set by their own M/T in that domain. They don't know what to ask for (M gap), and they can't tell if AI's output is good (T gap). Worse, they don't know what they don't know.

The goal is NOT to turn them into a domain expert. It's to build the minimum M/T they need to drive AI at an expert level in the target domain.

## Prerequisites

### User Profile (soft dependency)

Check if `axis-user-profile.md` has been populated:

- **If populated**: Read it to understand the user's home domain, existing knowledge, and AI usage patterns.
- **If NOT populated**: Ask upfront:
  - "What's your background? What domain are you experienced in?"
  - "What new domain are you trying to use AI for? What kind of tasks?"
  - "How far have you gotten? What's working, what's hitting walls?"

### Output File

Results MUST be written to `axis-domain-expansion-{target}.md` (in the current working context — see SKILL.md's "User Data Files" section for location conventions), where `{target}` is a short label for the target domain (e.g., `axis-domain-expansion-software-dev.md`). Writing this file is mandatory — do NOT end the conversation turn without persisting the results.

If the file already exists, show the user the previous analysis and ask whether to refine it or start fresh.

## The Three-Step Process

### Step 1: Map the Target Domain's "AI-Driving M/T"

For the target domain, identify the M/T that an expert uses when driving AI — not the full expert knowledge, but specifically the subset that matters for AI-era work.

Organize this into three tiers:


**Tier 1 — Judgment Knowledge (驾驭层)**
The M/T that directly determines AI output quality. This is what the expert is actually "using" when they drive AI.

Examples (software dev domain):
- Knowing to ask about error handling and edge cases
- Sensing when an architecture is over-engineered or under-engineered
- Judging whether AI's code is secure, performant, maintainable
- Knowing when to split a task vs keep it together
- Recognizing technical debt in AI-generated code

**Tier 2 — Foundation Knowledge (支撑层)**
The concepts that Tier 1 depends on. You can't judge "is this architecture good" without understanding what coupling and cohesion mean. You can't sense edge cases without understanding how programs execute.

These are NOT execution skills (you don't need to write code). They're conceptual foundations that support judgment.

Examples (software dev domain):
- How programs execute (control flow, not syntax)
- What data structures are and why they matter (concepts, not implementation)
- How systems communicate (request-response, async, not protocol details)
- What state is and why it causes bugs
- What "separation of concerns" means and why it matters

**Tier 3 — Replaced Knowledge (已替代层)**
Knowledge the expert has but that AI has fully replaced. The user does NOT need to learn these.

Examples (software dev domain):
- Specific language syntax
- API documentation details
- Boilerplate patterns
- Build tool configuration
- Specific framework conventions

**How to generate this map:**
- Think from the expert's perspective: "When I drive AI in this domain, what knowledge am I actually relying on that a novice wouldn't have?"
- For each Tier 1 item, trace its dependencies: "What do you need to understand first to be able to judge this?"
- Be aggressive about Tier 3: if AI can reliably handle it without human judgment, it's Tier 3.

Output this map as a structured document with clear dependency links between Tier 2 → Tier 1.

### Step 2: Assess the User's Current Knowledge

From the user's home domain, identify what transfers:

**Direct transfers**: Knowledge that maps directly to the target domain.
- PM's requirements analysis → problem decomposition (M6)
- PM's user empathy → multi-perspective thinking (T1.4)
- Designer's visual hierarchy sense → code structure sense (partial)

**Partial transfers**: Knowledge that's related but needs bridging.
- PM understands "user flow" → can be bridged to "program flow" with some conceptual work
- PM understands "feature scope" → can be bridged to "module boundaries"

**No transfer**: Target domain knowledge with no analog in the home domain.
- Understanding of state and side effects (if coming from non-technical background)
- Understanding of type systems and data modeling (if coming from non-technical background)

**How to assess:**
- Don't just ask "do you know X?" — people don't know what they don't know.
- Instead, give them a concrete scenario from the target domain and observe:
  - What questions do they ask? (reveals what they know to look for)
  - What do they miss? (reveals blind spots)
  - What analogies do they reach for? (reveals transfer potential)
- 3-5 scenario-based probes are usually enough to map the landscape.

### Step 3: Generate the Learning Path

Compute the delta: Target M/T (Step 1) minus Current Knowledge (Step 2) = What needs to be learned.

Then organize into a dependency-ordered learning path:

**Principles:**

1. **Dependency order**: If understanding X requires understanding Y, Y comes first. Never ask someone to learn something whose prerequisites they don't have.

2. **Bridge from known**: Whenever possible, introduce new concepts by analogy to what the user already knows. "You know how in product design, changing one feature can break another feature's flow? In code, that's called coupling, and it's the same problem."

3. **Minimum viable depth**: For each item, specify how deep they need to go. Not "learn everything about databases" but "understand that data has structure, that structure has tradeoffs, and that AI needs you to specify the structure — you don't need to learn SQL."

4. **Judgment-oriented framing**: Frame every learning item in terms of the judgment it enables. Not "learn about error handling" but "learn enough about error handling that you can tell AI 'handle the case where the network is down and the case where the user input is invalid' instead of just hoping AI thinks of it."

5. **Checkpoint questions**: For each item, include 1-2 questions the user should be able to answer after learning it. These serve as self-verification and can be used by future axis skills for assessment.

**Output format:**

```markdown
## Learning Path: [Home Domain] → [Target Domain]

### Phase 1: Conceptual Foundations
Items that everything else depends on. Usually 3-5 items.

#### 1.1 [Concept Name]
- Why you need this: [which Tier 1 judgments this enables]
- Bridge from your experience: [analogy to home domain]
- Learn to this depth: [specific depth boundary]
- You're done when you can answer: [checkpoint question(s)]
- Suggested resources: [if known — optional]

#### 1.2 ...

### Phase 2: Core Judgment Skills
The Tier 1 M/T items, now that foundations are in place. Usually 5-8 items.

#### 2.1 [Judgment Skill Name]
- What this lets you do: [concrete AI-driving capability this unlocks]
- Depends on: [which Phase 1 items]
- Bridge from your experience: [analogy]
- Learn to this depth: [depth boundary]
- You're done when you can answer: [checkpoint question(s)]

### Phase 3: Advanced / Situational
Items that matter in specific situations, not every interaction. Can be learned on-demand.

#### 3.1 ...
```


## How to Conduct the Session

### Tone
- Collaborative and respectful. The user is an expert in their own domain — they're not "starting from zero," they're expanding.
- Never condescending about what they don't know. They haven't needed to know it until now.
- Emphasize transfer: "Your PM instincts are actually a huge advantage here — you already think in user flows, which maps directly to program flow."

### Flow

1. **Understand the situation** (5 min):
   - What's their home domain and expertise level?
   - What target domain are they expanding into?
   - What are they trying to do with AI in the target domain?
   - What's working? What's hitting walls?

2. **Probe with scenarios** (10-15 min):
   - Give 3-5 concrete scenarios from the target domain
   - Observe what they notice, what they miss, what analogies they use
   - This simultaneously maps their current knowledge AND demonstrates the kind of M/T they're missing

3. **Present the map** (5 min):
   - Show the three-tier knowledge map for the target domain
   - Highlight what they already have (transfers from home domain)
   - Highlight the gaps — frame as "here's what's causing the ceiling you're hitting"

4. **Generate the path** (10 min):
   - Walk through the learning path
   - For each item, explain WHY it matters (in terms of AI-driving capability)
   - Get their input: does the ordering make sense? Anything feel wrong?

5. **Write the output file**

### What NOT to Do
- Don't try to teach the target domain during this session. This is diagnosis + planning, not execution.
- Don't overwhelm with a 50-item learning list. The path should be 10-15 items max, organized in 3 phases.
- Don't be vague about depth. "Learn about databases" is useless. "Understand that data has structure and that you need to tell AI what structure you want" is actionable.
- Don't ignore the user's home domain expertise. It's their biggest asset — every bridge you can build from it saves learning time.

## Output File Format

Write to `axis-domain-expansion-{target}.md`:

```markdown
# Domain Expansion: [Home Domain] → [Target Domain]

> Generated: [date]
> User profile: (from axis-user-profile.md or session)
> Purpose: [what the user wants to do with AI in the target domain]

## Current State

### Home Domain Strengths
- [transferable strength]: [how it maps to target domain]
- ...

### Identified Gaps
- [gap]: [why it matters for AI-driving capability]
- ...

### Blind Spots Revealed by Probes
- [scenario]: [what the user missed and why it matters]
- ...

## Target Domain: AI-Driving M/T Map

### Tier 1 — Judgment Knowledge (what you need to be able to judge)
- [item]: [one-line description]
- ...

### Tier 2 — Foundation Knowledge (what supports the judgments)
- [item]: [one-line description] → supports: [which Tier 1 items]
- ...

### Tier 3 — Replaced by AI (you do NOT need to learn these)
- [item]: [why AI handles this]
- ...

## Learning Path

### Phase 1: Conceptual Foundations
(dependency-ordered, bridged from home domain)

#### 1.1 [Item]
- Why: [judgment it enables]
- Bridge: [analogy to home domain]
- Depth: [specific boundary]
- Checkpoint: [verification question(s)]

...

### Phase 2: Core Judgment Skills
...

### Phase 3: Advanced / Situational
...

## Next Steps
- [ ] Complete Phase 1 (estimated: [time])
- [ ] Complete Phase 2 (estimated: [time])
- [ ] Phase 3 items can be learned on-demand as you encounter them
- [ ] After completing Phase 1-2, consider re-running axis-domain-expansion to refine the path based on new understanding
```

## Integration

### With SKILL.md (axis-main)
SKILL.md routes here when:
- User says they want to use AI in a domain they're not expert in
- User describes hitting a ceiling when using AI for cross-domain tasks
- User asks "what do I need to learn to use AI for X"

### With axis-user-profile.md
- Reads axis-user-profile.md for home domain context (soft dependency)
- After session, updates axis-user-profile.md Coaching Notes with: "Domain expansion path generated: [home] → [target] on [date]"

### With axis-model / axis-taste
- The learning path items map to specific M and T sub-capabilities
- Future coaching sessions can reference the path: "You're working on item 2.3 from your learning path — let's practice that judgment skill on your current task"

### Future: axis-domain-expansion-learn
A future companion skill that takes the generated learning path and walks the user through it step by step, using AI as the teaching tool. Not in scope for current version.