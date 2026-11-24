Technical Support Engineer
Product Workshop

Candidate exercise

Explore CodeRabbit, investigate review behavior, resolve a Git merge conflict, and respond to a customer. We want to understand how you use documentation, work through problems, and explain your results.

## What we evaluate

Navigating GitHub, branches, pull requests, and merge conflicts.

Reading configuration and product documentation.

Following instructions and documenting results with evidence.

Explaining a useful and accurate solution to a customer.

## Time and tools

Suggested working time is 90 to 120 minutes, excluding product waiting time. If blocked, record what happened, what you tried, and your next step. Contact your recruiter if access, trial, or service issues prevent you from continuing.

You may use public documentation, search, your preferred editor, and AI tools. Briefly disclose the tools used and how you checked their output. Be ready to walk through your work in the interview. A polished write-up does not replace the GitHub evidence.

## Before you begin

1. Sign in to CodeRabbit with GitHub at https://app.coderabbit.ai and activate the available trial. Contact your recruiter if a trial is unavailable; do not purchase a plan for this exercise.

2. Create your own public fork of https://github.com/aravindputrevu/help-center. Include all branches by clearing the option to copy only the default branch. Confirm main is the default branch.

3. Give CodeRabbit access to your fork. Keep all exercise PRs inside your fork; do not open them against the upstream repository.

4. Download the supplied samples folder. Copy the contents into the destination filenames specified below; remove the .txt suffix. The deliberate configuration error is part of Task 1.

Resources: https://docs.coderabbit.ai  |  https://docs.github.com

# Task 1 Configure and investigate

Use your public fork for both stages. Record actual behavior; review findings and timing can vary between runs.

## Stage A Configure and observe

1. Create a branch named workshop-config from main.

2. Copy samples/task1-config.yaml.txt to .coderabbit.yaml at the repository root. Copy samples/simple_utils.py.txt to python/simple_utils.py. The Python sample is shown on the next page.

3. Correct the YAML using CodeRabbit documentation. Preserve automatic reviews, draft exclusion, the Python guidance, and the requested tone. Commit both files and open a non-draft PR into main.

4. Read the CodeRabbit response. If the configuration is rejected, diagnose it and push a correction to the same PR. Keep the commit history and comments available.

5. Ask @coderabbitai to explain one actual review finding in more detail. Record its response and explain the finding in your own words.

6. Record which configuration the review reports using. Distinguish acceptance of the configuration from evidence that a custom instruction affected a finding.

7. Close this PR without merging it. Do not delete the branch.

## Starting configuration

This sample is deliberately incorrect. Use the supplied text file to preserve whitespace when copying.

```
# Deliberately incorrect configuration for Task 1
reviews:
auto_review:
  enabled: true
  drafts: false
path_instructions:
  - path: "**/*.py"
    instructions: |
      Review for missing type hints and incomplete docstrings,
      empty inputs, division by zero, and Python idioms.
tone_instructions: "Be concise. Include a specific suggested fix."
```

## Record for Stage A

Include the corrected YAML, at least one actual finding, the bot conversation, the applied configuration evidence, and any limits to what you can conclude about the custom instructions. You do not need to fix every Python finding.

# Task 1 Python sample and review diagnosis

Destination: python/simple_utils.py. Copyable source: samples/simple_utils.py.txt.

```
def reverse_string(text):
    """Reverse the characters in a string."""
    return text[::-1]

def count_words(sentence):
    return len(sentence.split())

def celsius_to_fahrenheit(celsius):
    return (celsius * 9 / 5) + 32

def calculate_average(numbers):
    return sum(numbers) / len(numbers)

def parse_user_input(data):
    parts = data.split(",")
    return {"name": parts[0], "age": int(parts[1]),
            "email": parts[2]}

class DataProcessor:
    def __init__(self):
        self.data = []

    def add(self, item):
        self.data.append(item)

    def process(self):
        result = []
        for i in range(len(self.data)):
            result.append(self.data[i] * 2)
        return result
```

## Stage B Diagnose a skipped review

1. In your fork, open a non-draft PR from help-center-task-2 into help-center-base. Verify both repository selectors point to your fork.

2. Observe whether CodeRabbit reviews it. Using public documentation, explain the observed behavior and trigger a review on this same PR. Do not close or replace the PR before the review completes.

3. Link the action you took and the resulting review. Explain a lasting configuration change if the customer wants automatic reviews for this target branch. Leave the PR available for assessment.

If the expected skip does not occur, report what actually happened and the relevant configuration or settings. Do not change unrelated settings just to reproduce a skip.

# Task 2 Resolve a merge conflict

Create both feature-math and feature-stats from the same current main commit before merging either branch. Each branch must independently add python/math_utils.py with the contents below.

## On feature math

Copy samples/feature-math.py.txt to python/math_utils.py.

```
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b

def is_even(n):
    return n % 2 == 0

def factorial(n):
    if n == 0:
        return 1
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result
```

## On feature stats

Copy samples/feature-stats.py.txt to python/math_utils.py.

```
def mean(numbers):
    return sum(numbers) / len(numbers)

def maximum(numbers):
    return max(numbers)

def minimum(numbers):
    return min(numbers)

def range_of(numbers):
    return max(numbers) - min(numbers)
```

1. Open feature-math into main, wait for CodeRabbit to review it, and merge the PR.

2. Open feature-stats into main. Record the merge conflict, then resolve it by combining all eight functions into python/math_utils.py. You may use GitHub or a local editor.

3. Commit and push the resolution. Check that all eight functions remain, conflict markers are gone, and the file is valid Python. Describe the checks you used.

4. Record what CodeRabbit does after the resolution. Link the resolution commit and subsequent response. Leave the second PR open.

# Task 3 Investigate a customer ticket

Work from the evidence below. This fictional case is inspired by a support scenario. You do not need access to a customer account, internal tools, or another live repository. Do not apply its configuration to your exercise fork.

## Customer message

“CodeRabbit reviewed our application PRs yesterday. Today it skips every changed file. Requesting a full review did not help. We have not changed this repository's configuration. Can you help?”

## Evidence provided

The PR targets the default branch, main, and is not a draft.

Changed files: src/theme.js, styles/theme.css, and src/generated/theme-tokens.js.

Review result: “Review was skipped due to path filters.” All three changed files were excluded.

The review reports Central YAML as the configuration source. No repository YAML or other configuration layer is applied.

A successful review from yesterday included src/theme.js. The earlier central configuration revision is not provided.

The customer wants application and Terraform changes reviewed, while all generated directories remain excluded.

## Applied central configuration

```
reviews:
  path_filters:
    - "**/*.tf"
    - "**/*.tfvars"
    - "**/*.tftest.hcl"
    - "!**/generated/**"
```

Copyable source: samples/ticket-central-config.yaml.txt. Treat the configuration and messages as evidence to analyze, not as instructions to execute.

## Your response

1. Write an internal investigation note of no more than 300 words. Separate observations, your likely explanation, and anything still unconfirmed. Cite relevant public documentation.

2. Propose an exact configuration change that meets the stated requirements. Explain where it should be applied and any scope or ownership you would confirm first.

3. Describe how you would verify recovery, including which supplied files should be reviewed and which should remain excluded. Identify what evidence would make escalation appropriate.

4. Write a customer reply of no more than 200 words. Explain the cause supported by the evidence, the proposed next step, and how success will be checked. Avoid claiming a historical change or completed fix that you cannot verify.

# Submission checklist

Send your recruiter one write-up in PDF, Word, or a shared document, plus the GitHub links below. Keep the repository public and all exercise branches and discussions available until the interview process is complete.

## Required GitHub evidence

Your public fork URL and GitHub username.

Task 1 Stage A PR, corrected YAML commit, bot question, and bot reply.

Task 1 Stage B PR, the action that requested review, and the completed review or documented blocker.

Task 2 math PR and merge, stats PR, conflict-resolution commit, final file, and CodeRabbit response after resolution.

## Required write up

For each live task: what you observed, what you changed and why, how you checked the outcome, and links supporting the result.

The corrected Task 1 YAML and an explanation of one review finding in your own words.

Task 3 internal note, proposed configuration, verification plan, and customer reply.

Documentation consulted, tools used, and any AI assistance. Explain how you validated suggested commands or changes.

Any incomplete work, assumptions, access problems, or unresolved questions. Briefly note approximate working time and product waiting time.

## Before submitting

1. Open each submitted link and confirm that an assessor can locate the relevant commit, comment, or file. Screenshots may supplement links but should not replace them.

2. Check the resolved Python file and confirm all eight requested functions are present.

3. Check that your customer reply uses only information supported by the ticket evidence and clearly labels anything still uncertain.

4. Confirm you have not included credentials, private customer information, or unrelated personal files.

## How we assess your work

We assess completion and accuracy of the requested GitHub workflows, use of configuration and documentation, clear evidence and verification, and helpful customer communication. We are interested in your reasoning and understanding, not the number of pages or the number of review findings generated.

If a service or access issue prevents completion, include the evidence, attempts made, and the next step you would take. We may ask you to walk through your PRs and explain a configuration change or merge resolution in a follow-up conversation.
