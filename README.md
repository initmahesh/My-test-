# GitHub for Product Managers
### A Practical Guide for PMs Who Want to Work Like Engineers

---

## What is GitHub?

> **Think of GitHub as "Facebook for Developers"** — a social platform where developers share, collaborate on, and manage code projects. Your activity board shows how active you are, just like a social feed.

| Layer | What it is |
|---|---|
| **Git** | The engine — tracks every change to your code locally |
| **GitHub** | The platform — hosts your code in the cloud and adds collaboration tools on top of Git |

```
YOUR COMPUTER                    GITHUB (Cloud)
┌─────────────┐                 ┌──────────────────────┐
│             │   git push ───► │                      │
│  Local      │                 │   Remote Repository  │
│  Repository │ ◄─── git pull   │   (shared with team) │
│             │                 │                      │
└─────────────┘                 └──────────────────────┘
```

---

## Key Terms — Plain English for PMs

```
┌─────────────────────────────────────────────────────────────┐
│                        GITHUB                               │
│          The platform that hosts your codebase              │
│                                                             │
│   ┌─────────────┐     ┌─────────────┐     ┌─────────────┐  │
│   │ REPOSITORY  │     │   BRANCH    │     │   COMMIT    │  │
│   │             │     │             │     │             │  │
│   │ Project     │     │ Isolated    │     │ Snapshot    │  │
│   │ folder with │     │ copy for    │     │ of changes  │  │
│   │ full history│     │ new feature │     │ with a note │  │
│   └─────────────┘     └─────────────┘     └─────────────┘  │
│                                                             │
│   ┌─────────────┐     ┌─────────────┐     ┌─────────────┐  │
│   │    CLONE    │     │ PULL REQUEST│     │    ISSUE    │  │
│   │             │     │             │     │             │  │
│   │ Copy a repo │     │ Formal ask  │     │ Bug, feature│  │
│   │ to your     │     │ to merge    │     │ request, or │  │
│   │ computer    │     │ your work   │     │ feedback    │  │
│   └─────────────┘     └─────────────┘     └─────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

---

## How Git Works — The Core Loop

Every developer (and PM) follows this cycle:

```
                        ┌───────────────────────┐
                        │    REMOTE REPO        │
                        │    (GitHub.com)       │
                        └───────────┬───────────┘
                                    │
                  ┌─────────────────▼──────────────────┐
                  │            git clone                │
                  │     (copy repo to your machine)     │
                  └─────────────────┬──────────────────┘
                                    │
                        ┌───────────▼───────────┐
                        │    LOCAL REPO         │
                        │    (your computer)    │
                        └───────────┬───────────┘
                                    │
          ┌─────────────────────────▼──────────────────────────┐
          │                                                     │
          ▼                         ▼                          ▼
   ┌─────────────┐          ┌──────────────┐          ┌──────────────┐
   │  git branch │          │  git commit  │          │  git push    │
   │             │          │              │          │              │
   │ Create new  │ ──edit──►│ Save snapshot│ ────────►│ Upload to    │
   │ feature     │          │ with message │          │ GitHub       │
   │ branch      │          │              │          │              │
   └─────────────┘          └──────────────┘          └──────┬───────┘
                                                             │
                                                    ┌────────▼────────┐
                                                    │  PULL REQUEST   │
                                                    │                 │
                                                    │ Team reviews →  │
                                                    │ Approve → Merge │
                                                    └─────────────────┘
```

---

## Git vs GitHub — What's the Difference?

```
┌─────────────────────────────────────────────────────────────────────┐
│                        GIT vs GITHUB                                │
├────────────────────┬────────────────────────┬───────────────────────┤
│                    │        GIT             │       GITHUB          │
├────────────────────┼────────────────────────┼───────────────────────┤
│ What it is         │ Version control        │ Cloud platform built  │
│                    │ software (the engine)  │ on top of Git         │
├────────────────────┼────────────────────────┼───────────────────────┤
│ Where it lives     │ Your local machine     │ The internet          │
├────────────────────┼────────────────────────┼───────────────────────┤
│ Works standalone?  │ ✅ Yes                 │ ❌ Needs Git           │
├────────────────────┼────────────────────────┼───────────────────────┤
│ Main job           │ Track changes,         │ Collaborate, share,   │
│                    │ manage history         │ review, ship code     │
├────────────────────┼────────────────────────┼───────────────────────┤
│ PM analogy         │ Your product changelog │ Confluence + Jira,    │
│                    │ (local, private)       │ but for code (shared) │
├────────────────────┼────────────────────────┼───────────────────────┤
│ Key commands       │ commit, branch,        │ PR, Issues, Actions,  │
│                    │ merge, log, diff       │ Releases, Wiki        │
└────────────────────┴────────────────────────┴───────────────────────┘
```

> **One-liner:** Git tracks changes on your machine. GitHub is where your team sees them.

---

## Branching — The A/B Test Analogy for PMs

> A branch is like running an **A/B test on your codebase** — you isolate the experiment from the live product until it's proven and ready.

```
MAIN BRANCH (production — what users see)
────────────────────────────────────────────────────────►
    │               │                   │
    │               │                   │
    ▼               ▼                   ▼
feature/checkout  feature/onboarding  fix/login-bug
(Dev A working)   (Dev B working)     (Dev C working)

        ↓ Pull Request + Review ↓

────────────────────●───────────────────────────────────►
                  MERGE
              (feature ships)
```

**PM Takeaway:** Branching lets your team work on 5 things simultaneously without breaking the product. Each branch = one story/epic in flight.

---

## Pull Requests — Your Review Gate

> A Pull Request (PR) is the equivalent of a **design review or PRD sign-off** — a structured checkpoint before anything goes live.

```
  DEVELOPER                  REVIEWER                    PM / LEAD
  ─────────                  ────────                    ─────────

  1. Create branch
     git checkout -b
     feature/checkout
         │
         ▼
  2. Write code &
     commit changes
     git commit -m "..."
         │
         ▼
  3. Push to GitHub
     git push origin
     feature/checkout
         │
         ▼
  4. Open Pull Request ──────► 5. Review code           6. Check product impact
     • title + description       • read the diff            • acceptance criteria met?
     • link to ticket            • leave comments           • edge cases covered?
     • screenshots if UI    ◄─── • request changes          • approve or flag
                                      │
         ◄────────────────────────────┘
  7. Address feedback
     push more commits
         │
         ▼
  8. All checks pass? ─────────────────────────────────► 9. Final approve
     ✅ Tests green                                           │
     ✅ No conflicts                                          ▼
     ✅ Peer approved                                   10. MERGE
                                                         └── code ships to main
                                                         └── branch deleted
                                                         └── ticket closed
```

**PM Tip:** PRs have a description, linked issues, and comments — this is where your acceptance criteria lives in engineering workflow.

---

## Decentralized Codebase — Why It Matters to PMs

> Unlike a shared Google Doc, Git is **decentralized** — every contributor has a full copy of the project history. No single point of failure.

```
              ┌─────────────────────┐
              │   GITHUB (origin)   │
              │   Central source    │
              └──────┬──────┬───────┘
                     │      │
          ┌──────────┘      └──────────┐
          │                           │
    ┌─────▼──────┐             ┌──────▼─────┐
    │  Dev A     │             │  Dev B     │
    │  Full copy │             │  Full copy │
    │  of repo   │             │  of repo   │
    └────────────┘             └────────────┘
          │                           │
    ┌─────▼──────┐             ┌──────▼─────┐
    │  Dev C     │             │  PM / You  │
    │  Full copy │             │  Full copy │
    │  of repo   │             │  of repo   │
    └────────────┘             └────────────┘
```

---

## PM Use Cases on GitHub

### 1. Version Control → Track Product Iterations

```
v1.0 ──► v1.1 ──► v1.2 ──► v2.0
  │         │        │        │
checkout  search   filters  redesign
launched  added    shipped  launched

← full history, always recoverable →
```

### 2. Issues → Your Lightweight Backlog

```
┌─────────────────────────────────────────┐
│  GitHub Issues                          │
│                                         │
│  🔴 Bug:  Login fails on mobile  #142   │
│  🟡 Feature: Add CSV export     #138   │
│  🟢 Docs:  Update onboarding    #129   │
│                                         │
│  Labels │ Assignees │ Milestones        │
│  Comments │ Linked PRs                  │
└─────────────────────────────────────────┘
```

**PM Tip:** GitHub Issues + Milestones can replace basic Jira for small teams.

### 3. README → Your Living PRD

> The README is the first thing anyone sees in a repo. Think of it as the **one-pager every PM should own** — problem, context, how it works.

### 4. Commit Messages → Your Changelog

```
Bad commit:   "fixed stuff"
Good commit:  "fix: checkout flow skips address validation for guest users (#142)"

                ↑                ↑                            ↑
             type           clear description            issue linked
```

**PM analogy:** Every commit is a release note. If your team writes good commits, your changelog writes itself.

### 5. GitHub as Your Portfolio

```
Your GitHub Profile
┌────────────────────────────────────────────────────┐
│  @yourhandle                                        │
│                                                     │
│  Activity Graph  ████░░████████░░░░███████          │
│  (shows consistency — recruiters look at this)     │
│                                                     │
│  Pinned Repos:                                      │
│  ├── product-case-studies (PRDs, teardowns)        │
│  ├── ai-pm-resources (research, frameworks)        │
│  └── my-test- (this repo!)                         │
└────────────────────────────────────────────────────┘
```

---

## GitHub Actions — CI/CD in Plain English

> GitHub Actions = **automated quality gates**. Every time code is pushed, GitHub can automatically run tests, checks, and deployments.

```
Developer pushes code
        │
        ▼
┌───────────────────┐
│  GitHub Actions   │
│  (triggered auto) │
├───────────────────┤
│  ✅ Run tests      │
│  ✅ Check style    │
│  ✅ Build app      │
│  ✅ Deploy to prod │
└───────────────────┘
        │
        ▼
   Pass → Ships     Fail → Blocked (notifies team)
```

**PM Takeaway:** When engineers say "CI/CD pipeline," this is it. It's your automated regression test before every release.

---

## Tools You'll Use

| Tool | What it's for | PM uses it to... |
|---|---|---|
| **GitHub.com** | Browse repos, PRs, issues | Review work, track releases, manage docs |
| **VS Code** | Edit files locally | Write PRDs in repo, edit README, read code |
| **Git (terminal)** | Run git commands | Clone, branch, commit, push |
| **GitHub CLI** | Git + GitHub from terminal | Faster PR creation, issue management |

---

## Quick Reference — Commands PMs Actually Use

```bash
# Get a copy of the repo on your machine
git clone https://github.com/org/repo.git

# See what branch you're on
git status

# Create a new branch (e.g. for a new doc or PRD)
git checkout -b docs/q2-roadmap

# Stage your changes
git add .

# Save a snapshot with a message
git commit -m "docs: add Q2 roadmap to product folder"

# Upload to GitHub
git push origin docs/q2-roadmap
```

---

## Agile Mindset: Consistency Over Perfection

> GitHub rewards **iteration** — small, frequent commits over infrequent big ones. This is the same as shipping MVPs over waiting for perfect.

```
❌ Wrong approach:          ✅ Right approach:
Work 3 weeks in silence     Commit daily, even small changes
Push 500-line dump          PRs stay small + reviewable
One giant PR                Team sees progress in real time
Merge conflicts everywhere  Fewer conflicts, faster reviews
```

---

*Built with notes from the PM Dev Tools Workshop. Next step: open VS Code, clone this repo, and make your first commit.*
