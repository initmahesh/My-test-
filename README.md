# GitHub for Product Managers — From Zero to Pro

A practical tutorial for PMs who want to work inside codebases, speak the language of engineers, and use GitHub as a competitive edge in interviews, stakeholder communication, and day-to-day product work.

---

## Why GitHub Matters for PMs

GitHub is where the product actually gets built. Everything — features, experiments, bug fixes, deployment pipelines — flows through it. When you understand GitHub, you can:

- Track what shipped, when, and why — without asking an engineer
- Write better specs by understanding how code is structured
- Review PRs and catch scope creep or missing requirements before merge
- Use your GitHub profile as a product portfolio that shows real shipping velocity
- Interview with confidence when asked "tell me about your technical depth"

---

## What Is GitHub?

GitHub is a cloud-based platform that stores and manages code. It's built on top of **Git**, a version control system that tracks every change ever made to a file.

Think of it this way:

| Analogy | GitHub Equivalent |
|---|---|
| Google Drive | Repository (code storage) |
| "Track Changes" in Docs | Git version control |
| Comment-and-suggest in Docs | Pull Request review |
| Folder with version history | Branch |
| Save + label a doc version | Commit |

Big companies (Google, Microsoft, Airbnb) and solo developers all use it. It's the Facebook for developers — you can see who's active, what they're building, and how they collaborate.

---

## Core Concepts: The PM's Cheat Sheet

### Repository (Repo)
A project folder that tracks all code and its full change history. Every project lives in a repo. You can have one repo per product, or one repo per team.

**PM takeaway:** Repos are where your roadmap becomes code. Understanding a repo's structure tells you how modular (or tangled) your product is.

### Branch
A parallel version of the codebase for isolated development. The main branch (`main` or `master`) is what's live in production. Engineers create feature branches to build without breaking the live product.

**PM takeaway:** Branches map directly to your product experiments. An A/B test? Two branches. A risky new feature? Its own branch until it's proven.

```
main (production)
 ├── feature/checkout-redesign
 ├── experiment/new-onboarding-flow
 └── fix/payment-bug
```

### Commit
Saving a snapshot of changes with a message explaining what changed and why. Every commit is timestamped and attributed to a person.

**PM takeaway:** Commit messages are a living changelog. Good commit messages make retrospectives, postmortems, and release notes dramatically easier. Push your team to write them for humans, not just machines.

Good commit message:
```
Add confidence score to contract review output

Closes #142 — users were unsure whether to trust the AI output.
Score now shows 0–100% with color coding.
```

Bad commit message:
```
fix stuff
```

### Clone
Copying a repository from GitHub to your local machine so you can view or edit files. You only need to do this once per project.

```bash
git clone https://github.com/your-org/your-repo.git
```

### Pull / Push
- **Pull** — download the latest changes from GitHub to your local machine
- **Push** — upload your local changes back to GitHub

```bash
git pull   # get latest from GitHub
git push   # send your changes to GitHub
```

### Pull Request (PR)
A formal request to merge a completed feature branch into `main`. PRs are where code gets reviewed, discussed, and approved before it goes live.

**PM takeaway:** PRs are the gate between "built" and "shipped." They're where you can catch missing requirements, ask "does this match the spec?", and see exactly what's changing. Reading PRs is one of the highest-leverage habits a PM can build.

---

## Git vs. GitHub — What's the Difference?

| | Git | GitHub |
|---|---|---|
| What it is | Version control software | Cloud platform built on Git |
| Where it runs | Your local machine | The internet |
| What it does | Tracks changes in files | Hosts repos, manages collaboration, runs automations |
| Analogy | The engine | The car |

You can use Git without GitHub (local only). You cannot use GitHub without Git underneath it.

---

## The PM Workflow: Step by Step

This is the standard loop you'll use to make changes — editing a README, updating a spec file, or reviewing a PR.

### Step 1 — Clone the Repo (one time)
```bash
git clone https://github.com/your-org/your-repo.git
cd your-repo
```

### Step 2 — Create a Branch for Your Work
```bash
git checkout -b docs/update-prd-q2
```
Name branches descriptively. `docs/update-prd-q2` tells anyone what this branch is for.

### Step 3 — Make Your Changes
Edit files using VS Code (see below) or any text editor.

### Step 4 — Stage and Commit Your Changes
```bash
git add README.md
git commit -m "Update Q2 PRD with revised success metrics"
```

### Step 5 — Push to GitHub
```bash
git push origin docs/update-prd-q2
```

### Step 6 — Open a Pull Request
Go to GitHub in your browser → your repo → you'll see a banner to open a PR from your branch. Add a description, tag reviewers, and submit.

### Step 7 — Merge After Review
Once approved, merge the PR into `main`. Your changes are now in the main codebase.

---

## PM Use Cases — Where This Actually Helps You

### Version Control for Product Work
Track every iteration of a PRD, spec, or README. Roll back to any prior version. No more "which doc is the latest?" — GitHub is the source of truth.

### Commit Messages as a Changelog
Require your team to write meaningful commit messages. At sprint review or in a postmortem, you can reconstruct exactly what changed and when, without a meeting.

### Branching for Experiments
Map feature flags and A/B tests to branches. Each experiment is isolated — you can kill it cleanly without touching the rest of the product.

### Pull Requests as a Review Gate
Read PRs before they merge. Ask: "Does this implementation match the spec? Is the edge case handled? Is the error state designed?" You don't need to read the code line-by-line — read the description, the files changed, and the comments.

### Issues for Feedback Loops
GitHub Issues is a built-in bug/feature tracker. Link user feedback directly to issues. Tag issues with `bug`, `enhancement`, `PM-review`. Creates a closed loop between user signal and eng work.

### README and PRDs as Living Documentation
Your PRD lives in the repo, versioned alongside the code. When the spec changes, the commit history shows who changed it and why. No Confluence drift.

### GitHub Actions — CI/CD Without the Mystery
GitHub Actions automates testing and deployment. When code is pushed, tests run automatically. When tests pass, it deploys. As a PM, you don't need to configure this — but you should know:
- A red check mark on a PR = tests failing = don't merge
- A green check mark = safe to ship (technically)
- Failed deployment = check the Actions tab for the error log

### GitHub as Your Portfolio
Your GitHub profile shows contribution activity — every commit, PR, and repo you touch. For PM interviews, a profile with real shipped work is more convincing than a slide deck of case studies.

---

## VS Code — Your Code Editor

VS Code (Visual Studio Code) is a free code editor by Microsoft. It's what most engineers use day-to-day. You don't need to write code to benefit from it — it's excellent for:

- Reading and editing Markdown files (PRDs, READMEs, specs)
- Navigating a codebase to understand product structure
- Viewing Git history and diffs visually with the built-in Git panel
- Using GitHub Copilot or Claude integrations for AI-assisted writing

**Install:** [code.visualstudio.com](https://code.visualstudio.com) — free, Mac/Windows/Linux.

Once installed, open a repo folder:
```bash
code /path/to/your-repo
```
Or open VS Code and use File → Open Folder.

---

## Quick Reference: Commands You'll Actually Use

```bash
# Setup (one time per machine)
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Start working
git clone <repo-url>          # copy repo to your machine
git pull                      # get latest changes

# Make changes
git checkout -b <branch-name> # create and switch to a new branch
git status                    # see what files you've changed
git add <filename>            # stage a file for commit
git add .                     # stage all changed files
git commit -m "message"       # save a snapshot with a label

# Share your work
git push origin <branch-name> # send your branch to GitHub

# Catch up with teammates
git pull origin main          # pull latest from main into your branch
```

---

## Interview: How to Talk About GitHub as a PM

When an interviewer asks about your technical depth, these are the answers that land:

**"How do you work with engineers day-to-day?"**
> "I review PRs before merge to verify the implementation matches the spec. I use commit history to prep for retrospectives and track what shipped between releases."

**"Are you technical?"**
> "I work in GitHub daily — I track issues, write and version specs in the repo, and I know enough to read a PR diff and ask the right questions. I don't write production code, but I stay close to the codebase."

**"Tell me about a time you caught a bug or requirement gap."**
> "I was reviewing a PR before merge and noticed a missing empty state for the case where search returns zero results. The spec covered the happy path but not the error state — caught it before it shipped."

---

## What to Do This Week

1. Create a free GitHub account at github.com
2. Install VS Code and Git
3. Clone a public repo (try `github.com/github/docs`) — just to see how it works
4. Create your own repo, add a README with your product philosophy
5. Make a change, commit it, push it — do the full loop once
6. Find an open-source PM-adjacent project and read 3 pull requests

---

## Glossary

| Term | Definition |
|---|---|
| Repository | Project folder with full change history |
| Clone | Copy a repo to your local machine |
| Branch | Isolated version of code for parallel development |
| Commit | Saved snapshot of changes with a message |
| Pull | Download latest changes from GitHub |
| Push | Upload local changes to GitHub |
| Pull Request (PR) | Request to merge a branch + code review gate |
| Merge | Combining a branch's changes into another branch |
| Main / Master | The primary branch — what's live in production |
| Issue | A tracked bug, feature request, or task |
| GitHub Actions | Automated workflows (testing, deployment) |
| CI/CD | Continuous Integration / Continuous Deployment — automated build-test-deploy pipeline |
| Git | The version control system underneath GitHub |
| Fork | Your own copy of someone else's repo |
| README | The front page of a repo — what it is and how to use it |
