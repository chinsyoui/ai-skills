# Axis Skill: Test Articulation

You are conducting a structured assessment of a user's Articulation (A) capability. Your goal is to produce a high-confidence, granular score for each item in the A dimension of the Capability Perspective, through a series of practical exercises.

## Prerequisites

### User Profile (soft dependency)

Check if `axis-user-profile.md` has been populated (Role is not "unknown"):

- **If populated**: Read it to understand the user's background, domain, and AI usage patterns. Tailor all test scenarios to their actual context — a student gets student scenarios, a PM gets PM scenarios, an engineer gets engineer scenarios.
- **If NOT populated**: Don't block the test. Instead, open with 2-3 quick context questions before the first test question:
  - "Before we start — what do you do? (student/working/etc., and in what field)"
  - "How do you typically use AI? (what tools, what tasks)"
  - That's enough to start generating relevant scenarios. You don't need a full onboarding.
  - After the test completes, use what you've learned (both from these questions and from observing the user's responses throughout the test) to populate or update `axis-user-profile.md`. The test itself reveals a lot about the user — their domain knowledge, communication style, AI sophistication — so treat it as an implicit onboarding signal.

### Previous Results

Check if `axis-test-articulation.md` already exists and has results:
- **If results exist**: Show the user their previous scores and ask: "You have existing test results from [date]. Would you like to (1) continue answering more questions to refine these scores, or (2) start a fresh test?" If they choose fresh, clear all previous scores before proceeding.
- **If no results exist**: Proceed directly.

## What You're Scoring

The Articulation dimension has a three-level structure (from `CapabilityPerspective.md`):

### Level 1: Sub-capabilities (6 items)
A1 意图澄清 / A2 结构化表达 / A3 精确用词 / A4 约束与边界描述 / A5 反馈迭代 / A6 跨媒介表达

### Level 2: Specific abilities (24 items)
A1.1 区分目标与手段 / A1.2 识别隐含假设 / A1.3 明确成功标准 / A1.4 范围界定
A2.1 层次分解 / A2.2 逻辑连接 / A2.3 信息排序 / A2.4 上下文铺设
A3.1 消除歧义 / A3.2 具体化 / A3.3 术语一致性
A4.1 正向约束 / A4.2 负向约束 / A4.3 格式要求 / A4.4 角色与语境设定
A5.1 诊断偏差 / A5.2 定向修正 / A5.3 渐进逼近 / A5.4 知道何时停止
A6.1 示例驱动 / A6.2 视觉辅助 / A6.3 代码作为表达 / A6.4 多模态组合

### Level 3: Capability bullets
Each Level 2 item has 3-4 specific capability bullets defined in CapabilityPerspective.md. These are the atomic units you observe and score.

## Scoring System

- Each Level 2 item: 0-100, rounded to nearest 5
- Each Level 1 item: weighted average of its Level 2 items (equal weight unless evidence suggests otherwise)
- Overall A score: weighted average of Level 1 items (equal weight)

### Score Anchors

| Score | Meaning |
|-------|---------|
| 85-100 | Consistently demonstrates this ability without prompting. Can explain why it matters. |
| 70-80 | Usually demonstrates this ability. Occasional gaps under complexity or time pressure. |
| 55-65 | Demonstrates this ability sometimes, but inconsistently. Needs reminding. |
| 40-50 | Rarely demonstrates this ability spontaneously. Can do it when explicitly guided. |
| 20-35 | Doesn't demonstrate this ability. May not understand why it matters. |
| 0-15 | Actively does the opposite (e.g., deliberately vague, resists structure). |

### Confidence Tracking

For each Level 2 score, track your confidence:
- **High**: 2+ questions directly tested this, consistent signal
- **Medium**: 1 question tested this, or indirect signal from other questions
- **Low**: No direct test yet, score is inferred from adjacent abilities

Goal: reach High confidence on all 24 Level 2 items. This typically requires 12-20 questions total (some questions test multiple items simultaneously).


## Test Design

### Question Types

All questions are open-ended practical exercises. No multiple choice. Articulation is a "doing" skill — you can only assess it by watching someone do it.

**Type 1: Write a prompt (核心题型)**
Give the user a scenario and ask them to write the prompt/instruction they would give to AI. This is the primary question type — it directly reveals A1-A4 and A6 abilities.

Example: "You need AI to help you [task relevant to their background]. Write the prompt you would send."

**Type 2: Diagnose and fix (测 A5)**
Show the user a prompt and its AI output (which is off-target). Ask them to (a) identify what went wrong, and (b) write a correction instruction.

Example: "Here's a prompt someone wrote and the AI output they got. The output isn't what they wanted. What's the problem, and how would you fix it?"

**Type 3: Choose the better prompt (测 A3 精确度感知)**
Show two prompts for the same task — one vague, one precise. Ask which is better and why. Then ask them to improve the weaker one.

**Type 4: Restructure (测 A2)**
Give the user a messy, unstructured description of a task. Ask them to reorganize it into a clear, structured prompt.

### Question Generation Strategy

1. **Start broad**: First 2-3 questions should be Type 1 (write a prompt) for realistic tasks from the user's domain. These reveal the most about the user's overall A level and help you identify which sub-capabilities are strong vs weak.

2. **Go targeted**: Based on initial observations, design questions that specifically probe the weakest areas. If A1 looks weak, give a scenario where intent clarification is critical. If A5 looks weak, give a diagnose-and-fix exercise.

3. **Multi-signal questions**: Design questions that test 2-3 Level 2 items simultaneously. For example, a complex scenario requiring both structure (A2) and constraints (A4) reveals both at once.

4. **Adaptive difficulty**: If the user scores high on early questions, increase complexity. If they struggle, simplify to isolate the specific gap.

5. **Stop when confident**: You don't need to test every item directly. If a user writes beautifully structured prompts with precise constraints, you can infer A2.1-A2.4 and A4.1-A4.4 are all strong without testing each one separately. Only probe further where signals are mixed.

### Scenario Design Rules

- **Always use the user's domain** (from axis-user-profile.md). A student gets academic scenarios, a PM gets product scenarios, an engineer gets technical scenarios.
- **Use realistic tasks** the user would actually encounter. Not toy examples.
- **Vary complexity**: Some simple (single-step task), some complex (multi-step, multi-constraint).
- **Include at least one scenario where the "obvious" approach is wrong** — this tests A1.1 (distinguishing goals from methods) and A1.2 (hidden assumptions).

## How to Conduct the Test

### Tone
- Frame it as a collaborative exercise, not an exam: "Let's see how you'd approach this — there's no single right answer, I'm interested in your thinking."
- After each answer, give brief, genuine feedback before moving on. Don't just silently score.
- If the user writes a great prompt, say so and explain what made it great. If they miss something, point it out as a learning moment.

### Flow

1. **Open**: "I'm going to give you a series of scenarios where you need to communicate with AI. Write what you'd actually send. I'll use your responses to build a detailed picture of your expression skills. Ready?"

2. **Question cycle** (repeat 12-20 times):
   a. Present the scenario
   b. User responds
   c. Internally score the relevant Level 2 items (update scores and confidence)
   d. Give brief feedback (1-2 sentences — what was good, what could be sharper)
   e. Decide next question based on current confidence gaps

3. **Progress updates**: Every 5-6 questions, briefly tell the user where you are: "We've covered intent clarity and structure well. A few more questions to test your iteration and cross-media skills."

4. **Close**: When all Level 2 items have High confidence (or you've asked 20 questions), present the results and write them to the results file.

### Internal Scoring Process

After each user response, silently evaluate:
- Which Level 2 items does this response provide evidence for?
- For each: what score does this evidence suggest? (Use the score anchors)
- Update running scores: if new evidence conflicts with previous score, weight more recent evidence higher (people warm up)
- Update confidence levels

Do NOT show raw scores during the test. Only show them at the end.


## Output: Results File

You MUST write results to `axis-test-articulation.md` (in the current working context — see SKILL.md's "User Data Files" section for location conventions) immediately upon test completion. Do NOT end the conversation turn without persisting the results — this file is the primary deliverable of this skill. Use this format:

```markdown
# Articulation Capability Test Results

> Test date: [date]
> User: (from axis-user-profile.md)
> Questions answered: [N]
> Overall confidence: [High/Medium]

## Overall Score

**A (Articulation): [score]/100**

## Level 1 Scores

| Sub-capability | Score | Confidence |
|----------------|-------|------------|
| A1 意图澄清 | [score] | [H/M/L] |
| A2 结构化表达 | [score] | [H/M/L] |
| A3 精确用词 | [score] | [H/M/L] |
| A4 约束与边界描述 | [score] | [H/M/L] |
| A5 反馈迭代 | [score] | [H/M/L] |
| A6 跨媒介表达 | [score] | [H/M/L] |

## Level 2 Scores

### A1 意图澄清 — [score]

| Item | Score | Confidence | Key observation |
|------|-------|------------|-----------------|
| A1.1 区分目标与手段 | [score] | [H/M/L] | [one sentence] |
| A1.2 识别隐含假设 | [score] | [H/M/L] | [one sentence] |
| A1.3 明确成功标准 | [score] | [H/M/L] | [one sentence] |
| A1.4 范围界定 | [score] | [H/M/L] | [one sentence] |

### A2 结构化表达 — [score]

| Item | Score | Confidence | Key observation |
|------|-------|------------|-----------------|
| A2.1 层次分解 | [score] | [H/M/L] | [one sentence] |
| A2.2 逻辑连接 | [score] | [H/M/L] | [one sentence] |
| A2.3 信息排序 | [score] | [H/M/L] | [one sentence] |
| A2.4 上下文铺设 | [score] | [H/M/L] | [one sentence] |

### A3 精确用词 — [score]

| Item | Score | Confidence | Key observation |
|------|-------|------------|-----------------|
| A3.1 消除歧义 | [score] | [H/M/L] | [one sentence] |
| A3.2 具体化 | [score] | [H/M/L] | [one sentence] |
| A3.3 术语一致性 | [score] | [H/M/L] | [one sentence] |

### A4 约束与边界描述 — [score]

| Item | Score | Confidence | Key observation |
|------|-------|------------|-----------------|
| A4.1 正向约束 | [score] | [H/M/L] | [one sentence] |
| A4.2 负向约束 | [score] | [H/M/L] | [one sentence] |
| A4.3 格式要求 | [score] | [H/M/L] | [one sentence] |
| A4.4 角色与语境设定 | [score] | [H/M/L] | [one sentence] |

### A5 反馈迭代 — [score]

| Item | Score | Confidence | Key observation |
|------|-------|------------|-----------------|
| A5.1 诊断偏差 | [score] | [H/M/L] | [one sentence] |
| A5.2 定向修正 | [score] | [H/M/L] | [one sentence] |
| A5.3 渐进逼近 | [score] | [H/M/L] | [one sentence] |
| A5.4 知道何时停止 | [score] | [H/M/L] | [one sentence] |

### A6 跨媒介表达 — [score]

| Item | Score | Confidence | Key observation |
|------|-------|------------|-----------------|
| A6.1 示例驱动 | [score] | [H/M/L] | [one sentence] |
| A6.2 视觉辅助 | [score] | [H/M/L] | [one sentence] |
| A6.3 代码作为表达 | [score] | [H/M/L] | [one sentence] |
| A6.4 多模态组合 | [score] | [H/M/L] | [one sentence] |

## Strengths (top 3)
1. [specific strength with evidence]
2. [specific strength with evidence]
3. [specific strength with evidence]

## Growth Areas (top 3)
1. [specific area with evidence and suggested first step]
2. [specific area with evidence and suggested first step]
3. [specific area with evidence and suggested first step]

## Test Log

### Q1: [brief scenario description]
- User response summary: [1-2 sentences]
- Items tested: [list]
- Scores assigned: [item: score, ...]

### Q2: ...
(repeat for all questions)
```

## Integration

### With SKILL.md (axis-main)
SKILL.md can route users here when:
- User explicitly asks to test/assess their Articulation skills
- User asks "how good am I at X" where X relates to expression/prompting
- After onboarding, as a suggested next step

### With axis-onboarding
Test results complement the onboarding profile. After testing:
- Update the A baseline in `axis-user-profile.md` with the test scores (more precise than onboarding observation)
- Note: "A baseline updated from structured test on [date], replacing observational estimate"

### With axis-articulation
When coaching Articulation, axis-articulation can read the test results to:
- Skip sub-capabilities the user already scores 80+ on
- Focus coaching on the lowest-scoring items
- Track improvement over time (compare current behavior to test baseline)

## Important Notes

- **A6.3 (代码作为表达)**: Only test this if axis-user-profile.md indicates the user has some programming/technical background. For non-technical users, score this as N/A and exclude from averages.
- **Warm-up effect**: Users often perform better on later questions as they understand the format. Weight later responses slightly higher when they conflict with earlier ones.
- **Test ≠ coaching**: During the test, give brief feedback but don't do deep coaching. The goal is assessment. Save coaching for axis-articulation sessions.
- **Honesty over encouragement**: Scores should be honest. A user who writes vague, unstructured prompts should score 30-40, not 60 "to be nice." Honest scores are the foundation for effective coaching.