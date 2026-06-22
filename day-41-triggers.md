# Day 41 - Triggers and Matrix Builds
## What are GitHub Actions Triggers?
Triggers decide WHEN a workflow should run automatically.
Think of it like a doorbell - the bell rings only when someone presses the button.
Similarly, a workflow runs only when a specific event happens.

---

## Task 1: PR Trigger (pull_request)

### What it does
This workflow runs automatically when someone opens or updates a Pull Request on the master branch.

### Step-by-step explanation


### Flow
1. Developer creates a new branch
2. Pushes commit to that branch
3. Opens a PR on GitHub targeting master
4. GitHub detects pull_request event
5. This workflow runs automatically
6. PR page shows green check or red cross

---

## Task 2: Scheduled Trigger (cron)

### What it does
This workflow runs automatically at a fixed time every day - like an alarm clock.

### Step-by-step explanation
Scheduled run at: Mon Jun 22 06:15:59 UTC 2026

### Cron Expression Guide
| Expression | Meaning |
|------------|---------|
| 0 0 * * *  | Every day at midnight UTC |
| 0 9 * * 1  | Every Monday at 9 AM UTC  |
| 0 9 * * 1  | Answer for Task 2 question |

### Cron Format Explained
- Position 1 = Minute (0-59)
- Position 2 = Hour (0-23)
- Position 3 = Day of month (1-31)
- Position 4 = Month (1-12)
- Position 5 = Day of week (0=Sunday, 1=Monday ... 6=Saturday)

---

## Task 3: Manual Trigger (workflow_dispatch)

### What it does
This workflow only runs when YOU manually click the Run button in GitHub Actions tab.
You can also pass input values like choosing staging or production environment.

### Step-by-step explanation


### How to manually trigger
1. Go to your GitHub repo
2. Click Actions tab
3. Select Manual Workflow from left sidebar
4. Click Run workflow button on the right
5. Choose staging or production from dropdown
6. Click the green Run workflow button
7. Watch it run and print your chosen environment

---

## Task 4: Matrix Builds

### What it does
Run the SAME job across multiple versions and operating systems at the same time.
Instead of writing 6 separate jobs, you write 1 job with a matrix and GitHub runs all combinations.

### Step-by-step explanation


### How matrix works
matrix creates all combinations automatically:
- Python 3.10 + Ubuntu
- Python 3.10 + Windows
- Python 3.11 + Ubuntu
- Python 3.11 + Windows
- Python 3.12 + Ubuntu
- Python 3.12 + Windows

Total = 3 versions x 2 OS = 6 jobs run in parallel

---

## Task 5: Exclude and Fail-Fast

### What it does
- exclude: Skip specific combinations from the matrix
- fail-fast: false: Even if one job fails, let all other jobs finish

### Step-by-step explanation


### After exclude: 6 - 1 = 5 jobs total

### fail-fast true vs false
| Behavior | fail-fast: true (default) | fail-fast: false |
|----------|--------------------------|-----------------|
| One job fails | All other jobs cancelled immediately | All other jobs continue |
| Result | Saves time but missing test results | Full results for all combinations |
| Use when | Any failure is a blocker | You want to see all failures at once |

---
