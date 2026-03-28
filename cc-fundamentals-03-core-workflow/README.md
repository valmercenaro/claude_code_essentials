# The Core Workflow

> Plan it. Build it. Validate it. Review it. Ship it.

## Make It Your Own

After cloning, remove the original remote and create your own GitHub repository:

**Windows (PowerShell)**
```powershell
git remote remove origin
gh repo create cc-fundamentals-03-core-workflow --public --source=. --remote=origin --push
```

**Mac / Linux**
```bash
git remote remove origin
gh repo create cc-fundamentals-03-core-workflow --public --source=. --remote=origin --push
```

> **Prerequisite:** Install the [GitHub CLI](https://cli.github.com/) — `winget install GitHub.cli` (Windows) or `brew install gh` (Mac), then run `gh auth login` once.

---

## Before the Purpose

You can use Claude Code for one-off tasks, but the real power comes from a **consistent workflow**. When you follow the same phases every time, you:
- Catch problems early (before they become expensive)
- Build muscle memory (less thinking, more doing)
- Create documentation automatically (specs become your history)

This module teaches the 5-phase workflow that turns chaotic coding into predictable progress.

---

## Purpose

The Core Workflow is a structured approach to building features:

```
PLAN ──► BUILD ──► VALIDATE ──► REVIEW ──► COMMIT
  │         │          │           │          │
  ▼         ▼          ▼           ▼          ▼
Create    Write      Test       Check     Ship
spec      code       it         quality   it
```

Each phase has its own command. Each command produces specific outputs. The workflow is repeatable for any task.

---

## The 5 Phases

### Phase 1: PLAN (`/plan`)

**What**: Create a detailed specification before writing code
**Output**: `specs/todo/[feature-name].md`
**Why**: Thinking before typing prevents rework

```
/plan "Add user authentication with email/password"
```

### Phase 2: BUILD (`/build`)

**What**: Implement the plan
**Output**: Working code, plan moved to `specs/done/`
**Why**: Following a spec keeps you focused

```
/build specs/todo/user-auth.md
```

### Phase 3: VALIDATE (`/validate`)

**What**: Test that everything works
**Output**: Validation report, screenshots (optional)
**Why**: Catch bugs before users do

```
/validate
```

### Phase 4: REVIEW (`/review`)

**What**: Check implementation against the original spec
**Output**: Review report with approval/issues
**Why**: Ensure you built what was planned

```
/review specs/done/user-auth.md
```

### Phase 5: COMMIT (`/commit`)

**What**: Commit and push changes
**Output**: Git commit with descriptive message
**Why**: Save your work, share with team

```
/commit
```

---

## Workflow Recipes

Different tasks need different workflows. Here are the three most common patterns:

### Recipe 1: Quick Fix (~75% of tasks)

**When to use**: Bug fixes, small changes, low-risk updates

```
/plan "Fix button alignment on homepage"
/build specs/todo/fix-button.md
/validate
/commit
```

**Phases**: Plan → Build → Validate → Commit
**Skips**: Review (small changes don't need spec comparison)
**Success Rate**: ~75%

---

### Recipe 2: Standard Feature (~85% success)

**When to use**: New features, medium complexity, user-facing changes

```
/plan "Add search functionality to product list"
/build specs/todo/add-search.md
/validate
/review specs/done/add-search.md
/commit
```

**Phases**: Plan → Build → Validate → Review → Commit
**Skips**: None (full workflow)
**Success Rate**: ~85%

---

### Recipe 3: Full Workflow with Security (~95% success)

**When to use**: Authentication, payments, data handling, API endpoints

```
/plan "Add payment processing integration"
/build specs/todo/payment-integration.md
/validate
/security (optional - covered in Module 7)
/review specs/done/payment-integration.md
/commit
```

**Phases**: Plan → Build → Validate → [Security] → Review → Commit
**Includes**: Optional security audit before review
**Success Rate**: ~95%

---

## Why This Order?

| Order | Reason |
|-------|--------|
| Plan FIRST | Can't build without knowing what to build |
| Build SECOND | Need code before you can test it |
| Validate THIRD | Catch bugs while context is fresh |
| Review FOURTH | Compare against spec after validation passes |
| Commit LAST | Only ship working, reviewed code |

**The pattern**: Create → Execute → Verify → Ship

---

## The Specs Folder System

```
specs/
├── todo/           # Plans waiting to be built
│   └── feature.md  # Created by /plan
├── done/           # Completed plans
│   └── feature.md  # Moved here by /build
└── handoffs/       # Session state files
    └── 001-2026-01-24-feature.md
```

This folder structure automatically tracks your work:
- New plans appear in `todo/`
- After building, they move to `done/`
- You can see what's been completed by checking `done/`

---

## Visual Verification with Playwright

This module includes the Playwright MCP for visual verification:

**What it does**:
- Takes screenshots of your app
- Captures before/after states
- Provides visual proof that features work

**When to use**:
- During `/validate` for UI changes
- During `/review` to document working features

**Configuration**: Already set up in `.mcp.json`

---

## Commands Included

### Core Workflow Commands
| Command | Phase | Description |
|---------|-------|-------------|
| `/plan` | 1 | Create implementation specification |
| `/build` | 2 | Implement from spec file |
| `/validate` | 3 | Run tests and verify functionality |
| `/review` | 4 | Compare implementation to spec |
| `/commit` | 5 | Create git commit with message |

### Supporting Commands
| Command | Description |
|---------|-------------|
| `/prime` | Understand the codebase quickly |
| `/handoff` | Save session state for later |
| `/pickup` | Resume from previous session |
| `/install` | Install commands globally or to a project |

---

## Getting Started

1. Clone this repo
2. Run `/prime` to understand the codebase
3. Try the Quick Fix recipe on a small task
4. Graduate to Standard Feature for bigger work

---

## Quick Reference

**Minimum workflow**: Plan → Build → Validate → Commit
**Standard workflow**: Plan → Build → Validate → Review → Commit
**Full workflow**: Plan → Build → Validate → Security → Review → Commit

**Rule of thumb**:
- Small fix? Skip review.
- New feature? Include review.
- Security-sensitive? Add security check.

---

*Plan it. Build it. Validate it. Review it. Ship it.*
