# Claude Certified Architect Foundations (CCA-F) Study Plan

A 30-day plan at 2 hours per day, written for someone starting from zero knowledge of Claude. Work through the phases in order. Check off each task and concept as you master it, not just as you read it.

## Exam Facts

- 60 multiple choice questions, 4 options each, exactly 1 correct answer
- No guessing penalty, so never leave a question blank
- 120 minutes total, which is roughly 2 minutes per question
- Passing score is 720 out of 1000 scaled points
- Cost is 99 USD
- Scenario based: 6 scenarios exist and you are given 4 at random, so prepare for all 6
- The 6 scenarios are:
  1. Customer Support Resolution Agent
  2. Code Generation with Claude Code
  3. Multi-Agent Research System
  4. Developer Productivity
  5. Claude Code for CI/CD
  6. Structured Data Extraction

## Domain Weights

| Domain | Topic | Weight |
|:------|:------|:------|
| D1 | Agentic Architecture and Orchestration | 27% |
| D2 | Tool Design and MCP Integration | 18% |
| D3 | Claude Code Configuration and Workflows | 20% |
| D4 | Prompt Engineering and Structured Output | 20% |
| D5 | Context Management and Reliability | 15% |

D1 carries the most weight, so spend the most effort there. D2 through D4 are close together in the middle. D5 is the smallest but still worth roughly nine questions.

## Progress Tracker

- [ ] Phase 1 Foundations (Days 1 to 4)
- [ ] Phase 2 D1 Agentic Architecture (Days 5 to 10)
- [ ] Phase 3 D2 Tool Design and MCP (Days 11 to 13)
- [ ] Phase 4 D3 Claude Code Configuration (Days 14 to 16)
- [ ] Phase 5 D4 Prompt Engineering and Structured Output (Days 17 to 19)
- [ ] Phase 6 D5 Context Management and Reliability (Days 20 to 22)
- [ ] Phase 7 Practice (Days 23 to 28)
- [ ] Phase 8 Final Review (Day 29)
- [ ] Day 30 Exam

Scenario readiness:

- [ ] Scenario 1 Customer Support Resolution Agent
- [ ] Scenario 2 Code Generation with Claude Code
- [ ] Scenario 3 Multi-Agent Research System
- [ ] Scenario 4 Developer Productivity
- [ ] Scenario 5 Claude Code for CI/CD
- [ ] Scenario 6 Structured Data Extraction

---

## Phase 1: Foundations (Days 1 to 4)

Goal: understand how a large language model works and how the Messages API is shaped before touching any agentic concepts.

### Concepts to master

- [ ] What a large language model is and that it predicts the next token
- [ ] What a token is and why text is measured in tokens rather than words
- [ ] What the context window is and that it has a fixed size
- [ ] The difference between the system prompt and user messages
- [ ] The structure of a Messages API call: system, messages array, roles
- [ ] The role values user and assistant and how a conversation alternates
- [ ] What stop_reason is and why it matters for control flow
- [ ] The difference between stop_reason end_turn and stop_reason tool_use
- [ ] That the model has no memory between calls, so all context must be resent every time

### Tasks

- [ ] Take the [AI Fluency Framework Foundations](https://anthropic.skilljar.com/ai-fluency-framework-foundations) course
- [ ] Take the [Claude 101](https://anthropic.skilljar.com/claude-101) course
- [ ] Take the [Claude with the Anthropic API](https://anthropic.skilljar.com/claude-with-the-anthropic-api) course
- [ ] Write in your own words what happens on a single API call from request to stop_reason
- [ ] Explain to yourself why a stateless model needs the full history resent each turn

---

## Phase 2: D1 Agentic Architecture and Orchestration (Days 5 to 10)

Goal: the largest domain at 27%. Understand the agentic loop, multi-agent coordination, and hooks.

### The agentic loop and control flow

- [ ] How the agentic loop works: call model, check stop_reason, run tools, send results, repeat
- [ ] That stop_reason tool_use means run the tool and continue the loop
- [ ] That stop_reason end_turn means the task is complete and the loop ends
- [ ] Use stop_reason, not text content, to decide whether the loop continues

### Loop anti-patterns to recognize and avoid

- [ ] Parsing assistant text to decide control flow instead of reading stop_reason
- [ ] Using arbitrary iteration caps as the primary stopping mechanism
- [ ] Treating text phrases like "done" as a completion signal instead of stop_reason

### Multi-agent coordination

- [ ] The hub-and-spoke pattern with a coordinator and subagents
- [ ] That subagents do NOT inherit the coordinator context, so context must be passed explicitly
- [ ] The Task tool and that allowedTools must include Task for delegation to work
- [ ] What an AgentDefinition is and what it specifies
- [ ] Running parallel subagents by issuing multiple Task calls in a single response

### Hooks

- [ ] The difference between PreToolUse and PostToolUse hooks
- [ ] That hooks give deterministic guarantees while prompts are only probabilistic
- [ ] When to choose a hook over an instruction in a prompt

### Orchestration strategy

- [ ] Prompt chaining versus dynamic decomposition and when each fits
- [ ] Using --resume to continue a session
- [ ] Using fork_session to branch from an existing session

### Tasks

- [ ] Take the [Introduction to Subagents](https://anthropic.skilljar.com/introduction-to-subagents) course
- [ ] Sketch a hub-and-spoke design for Scenario 3 Multi-Agent Research System
- [ ] List the loop anti-patterns from memory and write the correct pattern for each
- [ ] Write the difference between PreToolUse and PostToolUse in one sentence each

---

## Phase 3: D2 Tool Design and MCP Integration (Days 11 to 13)

Goal: 18%. Understand how Claude selects tools, how to design tool errors, and how MCP is configured.

### Tool design and selection

- [ ] Tool descriptions are the primary mechanism Claude uses to select a tool
- [ ] Fix bad tool selection with better descriptions, not with an extra routing layer
- [ ] Split a generic tool into specific tools when selection is ambiguous
- [ ] Too many tools degrades selection, so keep the set small, roughly 4 to 5
- [ ] tool_choice modes: auto, any, and forced, and when each is appropriate

### Tool errors

- [ ] The isError flag on a tool result
- [ ] errorCategory values: transient, validation, business, permission
- [ ] The isRetryable flag and how it relates to errorCategory
- [ ] The difference between an access failure and a valid empty result

### MCP configuration

- [ ] .mcp.json at project scope versus ~/.claude.json at user scope
- [ ] Environment variable expansion such as GITHUB_TOKEN in MCP config
- [ ] Using MCP resources for catalogs and reference data

### Built-in tools

- [ ] The built-in tools Read, Write, Edit, Bash, Grep, Glob
- [ ] When to use each built-in tool and when not to reach for Bash

### Tasks

- [ ] Take the [Introduction to Model Context Protocol](https://anthropic.skilljar.com/introduction-to-model-context-protocol) course
- [ ] Take the [Model Context Protocol Advanced Topics](https://anthropic.skilljar.com/model-context-protocol-advanced-topics) course
- [ ] Write a strong tool description and a weak one and explain the difference
- [ ] Map each errorCategory to whether it should be retried

---

## Phase 4: D3 Claude Code Configuration and Workflows (Days 14 to 16)

Goal: 20%. Understand CLAUDE.md, rules, commands, skills, and CI usage.

### CLAUDE.md and configuration files

- [ ] The CLAUDE.md hierarchy: user, project, and directory levels
- [ ] That user-level configuration is not shared through version control
- [ ] The @import syntax for pulling in other files
- [ ] .claude/rules/ with YAML frontmatter that scopes rules by path globs
- [ ] .claude/commands/ at project scope versus ~/.claude/commands/ at user scope

### Skills

- [ ] Skills live in .claude/skills/ with a SKILL.md file
- [ ] SKILL.md frontmatter fields: context:fork, allowed-tools, argument-hint
- [ ] When to use a skill versus putting instructions in CLAUDE.md

### Workflows

- [ ] Plan mode versus direct execution and when to use plan mode
- [ ] The Explore subagent for read-only codebase search
- [ ] The /memory command
- [ ] Session context isolation for independent review

### Claude Code in CI

- [ ] The -p or --print flag for non-interactive runs
- [ ] The --output-format json flag
- [ ] The --json-schema flag for structured CI output
- [ ] Iterative refinement, the interview pattern, and test-driven iteration

### Tasks

- [ ] Take the [Claude Code 101](https://anthropic.skilljar.com/claude-code-101) course
- [ ] Take the [Claude Code in Action](https://anthropic.skilljar.com/claude-code-in-action) course
- [ ] Take the [Introduction to Agent Skills](https://anthropic.skilljar.com/introduction-to-agent-skills) course
- [ ] Draft a CLAUDE.md outline for Scenario 4 Developer Productivity
- [ ] Write the exact CLI flags you would use for Scenario 5 Claude Code for CI/CD

---

## Phase 5: D4 Prompt Engineering and Structured Output (Days 17 to 19)

Goal: 20%. Understand prompting for reliability and producing structured data.

### Prompt engineering

- [ ] Explicit criteria beat vague instructions
- [ ] Few-shot examples and when they help
- [ ] That tool_use with JSON schemas eliminates syntax errors but not semantic errors

### Structured output

- [ ] tool_choice options for forcing structured output
- [ ] Nullable fields prevent fabrication by allowing a null instead of a guess
- [ ] The enum plus other-and-detail pattern for open-ended categories
- [ ] Retry-with-error-feedback and why retries fail when the information is absent from the source

### Batch processing

- [ ] The Message Batches API gives 50% cost savings
- [ ] The 24 hour processing window and that there is no SLA
- [ ] That batches do not support multi-turn tool calling
- [ ] The custom_id field for matching results to requests
- [ ] That batches are not for blocking workflows

### Review patterns

- [ ] Multi-instance review
- [ ] Multi-pass review

### Tasks

- [ ] Design a JSON schema for Scenario 6 Structured Data Extraction
- [ ] Write a prompt that uses nullable fields and the enum plus other pattern
- [ ] Explain why a retry will not fix a missing field that is absent from the source

---

## Phase 6: D5 Context Management and Reliability (Days 20 to 22)

Goal: 15%. Understand the context window in practice and how to keep agents reliable.

### Context window in practice

- [ ] What lives in the context window during an agent run
- [ ] The lost-in-the-middle effect where content in the middle gets less attention
- [ ] Progressive summarization loses numbers and dates, so keep a persistent case-facts block
- [ ] Trim verbose tool outputs before they fill the context

### Reliability and escalation

- [ ] Escalation triggers: an explicit human request, policy gaps, and no progress
- [ ] That sentiment and self-reported confidence are unreliable signals
- [ ] Structured error propagation through a system

### Recovery and persistence

- [ ] Scratchpad files for working state
- [ ] The /compact command
- [ ] Crash recovery using state manifests

### Data quality for extraction and research

- [ ] Field-level confidence scoring
- [ ] Stratified sampling for quality checks
- [ ] Claim-source mappings
- [ ] Conflict annotation when sources disagree
- [ ] Handling temporal data

### Tasks

- [ ] Write the three escalation triggers from memory for Scenario 1 Customer Support Resolution Agent
- [ ] Explain why a persistent case-facts block beats progressive summarization for dates and numbers
- [ ] List the data-quality techniques and tie each to Scenario 3 or Scenario 6

---

## Phase 7: Practice (Days 23 to 28)

Goal: convert knowledge into exam performance through repeated testing and hands-on work.

- [ ] Take the [official practice exam](https://anthropic.skilljar.com/claude-certified-architect-foundations-access-request), attempt 1 (Day 23)
- [ ] Review every wrong answer in your own words, attempt 1
- [ ] Take the [official practice exam](https://anthropic.skilljar.com/claude-certified-architect-foundations-access-request), attempt 2 (Day 25, one day gap)
- [ ] Review every wrong answer in your own words, attempt 2
- [ ] Take the [official practice exam](https://anthropic.skilljar.com/claude-certified-architect-foundations-access-request), attempt 3 (Day 27, one day gap)
- [ ] Review every wrong answer in your own words, attempt 3
- [ ] Complete official hands-on exercise 1
- [ ] Complete official hands-on exercise 2
- [ ] Complete official hands-on exercise 3
- [ ] Complete official hands-on exercise 4
- [ ] Drill weak domains on [CertSafari](https://certsafari.com/anthropic/claude-certified-architect)
- [ ] Re-walk all 6 scenarios and confirm each is checked in the tracker

---

## Phase 8: Final Review (Day 29)

Goal: consolidate, do not learn anything new.

- [ ] Reread the exam guide appendix
- [ ] Review your wrong-answer notes from all three practice attempts
- [ ] Do not study any new material
- [ ] Get a full night of sleep

---

## Day 30: Exam

- [ ] Arrive or log in early and check the testing setup
- [ ] Remember there is no guessing penalty, so answer every question
- [ ] Budget roughly 2 minutes per question and flag hard ones to revisit
- [ ] Take the exam

---

## Out of Scope

These topics are not on the exam. Do not spend study time on them.

- [ ] Fine-tuning
- [ ] API authentication and billing
- [ ] Hosting MCP infrastructure
- [ ] Anthropic internal architecture
- [ ] RLHF
- [ ] Embeddings and vector databases
- [ ] Computer use
- [ ] Vision
- [ ] Streaming implementation
- [ ] Rate limits and pricing
- [ ] OAuth details
- [ ] Cloud provider configuration
- [ ] Benchmarking
- [ ] Prompt caching internals
- [ ] Tokenization specifics

---

## Resources

### Courses (anthropic.skilljar.com)

- [AI Fluency Framework Foundations](https://anthropic.skilljar.com/ai-fluency-framework-foundations)
- [Claude 101](https://anthropic.skilljar.com/claude-101)
- [Claude with the Anthropic API](https://anthropic.skilljar.com/claude-with-the-anthropic-api)
- [Introduction to Subagents](https://anthropic.skilljar.com/introduction-to-subagents)
- [Introduction to Model Context Protocol](https://anthropic.skilljar.com/introduction-to-model-context-protocol)
- [Model Context Protocol Advanced Topics](https://anthropic.skilljar.com/model-context-protocol-advanced-topics)
- [Claude Code 101](https://anthropic.skilljar.com/claude-code-101)
- [Claude Code in Action](https://anthropic.skilljar.com/claude-code-in-action)
- [Introduction to Agent Skills](https://anthropic.skilljar.com/introduction-to-agent-skills)

### Documentation and exam access

- [Anthropic Documentation](https://docs.anthropic.com)
- [Exam access and official practice exam](https://anthropic.skilljar.com/claude-certified-architect-foundations-access-request)
- [CertSafari practice questions](https://certsafari.com/anthropic/claude-certified-architect)
