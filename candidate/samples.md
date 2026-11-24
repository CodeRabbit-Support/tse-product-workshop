# CodeRabbit TSE workshop samples

Use these copyable blocks with the exercise PDF. Copy only the contents inside each code block, preserving indentation. The destination file and branch are stated for each task.

## Task 1 Starting YAML

On workshop-config, copy this block to .coderabbit.yaml at the repository root. This configuration is deliberately incorrect. Correct it as instructed in the exercise.

```yaml
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

## Task 1 Python utility

On workshop-config, copy this block to python/simple_utils.py.

```python
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

## Task 2 Math branch

On feature-math, copy this block to python/math_utils.py. Create feature-math and feature-stats from the same main commit before merging either branch.

```python
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

## Task 2 Statistics branch

On feature-stats, copy this block to python/math_utils.py. This is the same destination path as on feature-math, with different contents; keep these changes on their separate branches until the conflict-resolution step.

```python
def mean(numbers):
    return sum(numbers) / len(numbers)

def maximum(numbers):
    return max(numbers)

def minimum(numbers):
    return min(numbers)

def range_of(numbers):
    return max(numbers) - min(numbers)
```

## Task 3 Customer configuration evidence

For analysis only. Do not copy this configuration into your exercise fork. Use it with the fictional ticket evidence in the exercise.

```yaml
reviews:
  path_filters:
    - "**/*.tf"
    - "**/*.tfvars"
    - "**/*.tftest.hcl"
    - "!**/generated/**"
```
