# Crafting Effective Prompts for Simple Tasks

Writing clear and structured prompts can dramatically improve the quality of output from Amazon Q Developer. In this section, we'll explore best practices for simple tasks, focusing on common scenarios such as debugging, code refactoring, unit testing, and code optimization.

## Scenario 1: Debugging

### Best Practice: Focus on Symptoms and State What You've Already Tried

When debugging, simply stating that something doesn't work may not always lead to the most effective solution. A clear debugging prompt should focus on explaining the symptoms clearly, allowing Amazon Q Developer to focus directly on the issue.

#### Formula for Debugging Prompts:

1. Provide context of your code: "I have a [type of code/function]"
2. Describe the symptoms: "It's supposed to [desired outcome] but [issue]"
3. Ask for root causes and fix: "Can you identify the root causes of [symptom] and provide a fix?"

#### Example: Debugging a JavaScript Function

**Bad Prompt:**
```
Fix this code:

function calculateTotal(items) {
  let total = 0;
  for (let i = 0; i < items.length; i++) {
    total += item.price;
  }
  return total;
}
```

**Why it's ineffective:**
- Lacks context about what the function should do
- Doesn't specify the symptoms or error
- Doesn't mention what's been tried already
- Doesn't provide enough information about the expected behavior

**Better Prompt:**
```
I have a JavaScript function that calculates the total price of items in a shopping cart. It's supposed to sum up the price of each item, but it's throwing a "item is not defined" error when I run it. Here's the code:

function calculateTotal(items) {
  let total = 0;
  for (let i = 0; i < items.length; i++) {
    total += item.price;
  }
  return total;
}

Can you identify the root cause of this error and provide a fix? I've checked that the items array is properly formatted with each object having a price property.
```

**Why it's effective:**
- Provides clear context about the function's purpose
- Specifies the exact error message
- Describes what's been checked already
- Includes details about the expected data structure

## Scenario 2: Code Refactoring

### Best Practice: Specify the Objective of Refactoring

If you are unsure about the specific issues in your code, you can use Amazon Q's "refactor" feature to perform an overall refactoring of your code. However, if you have a particular objective (e.g., improving performance, readability, or maintainability), you can craft a more specific prompt.

#### Formula for Refactoring Prompts:

1. Describe the current issue with the code: "My code works, but [specific problem]"
2. Describe the specific objective for refactoring: "I want to improve [specific objective]"
3. Provide the code snippet: "Here's the code: [code snippet]"

#### Example: Refactoring a Python Function

**Bad Prompt:**
```
Refactor this code:

def process_data(data):
    result = []
    for i in range(len(data)):
        if data[i] % 2 == 0:
            result.append(data[i] * 2)
        else:
            result.append(data[i] * 3)
    return result
```

**Why it's ineffective:**
- Doesn't specify what aspects need improvement
- Lacks context about the function's purpose
- No clear objective for the refactoring

**Better Prompt:**
```
I have a Python function that processes a list of numbers by multiplying even numbers by 2 and odd numbers by 3. The code works correctly, but I want to improve its readability and make it more Pythonic by using list comprehensions or other modern Python features. Here's the code:

def process_data(data):
    result = []
    for i in range(len(data)):
        if data[i] % 2 == 0:
            result.append(data[i] * 2)
        else:
            result.append(data[i] * 3)
    return result

Can you refactor this code to make it more concise and readable while maintaining the same functionality?
```

**Why it's effective:**
- Clearly explains the function's purpose
- Specifies the refactoring objective (readability and Pythonic style)
- Mentions specific techniques to consider (list comprehensions)
- Emphasizes that functionality must be maintained

## Scenario 3: Unit Testing

### Best Practice: Ask Amazon Q to List Unit Test Cases and Implement Them

You can have Amazon Q write your unit tests directly, saving you the effort of creating them manually.

#### Formula for Unit Testing Prompts:

1. Provide the Code: "Here's my [function or class] code: [paste code]"
2. Request Unit Test Suggestions: "Can you suggest some unit test cases for it?"

#### Example: Generating Unit Tests for a Python Function

**Effective Prompt:**
```
Here's my Python function that validates email addresses:

def validate_email(email):
    import re
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return bool(re.match(pattern, email))

Can you generate comprehensive unit tests for this function using pytest? Please include tests for valid emails, invalid emails, edge cases, and any potential issues you identify with the current implementation.
```

**Why it's effective:**
- Provides the complete function code
- Specifies the testing framework to use (pytest)
- Requests specific types of test cases (valid emails, invalid emails, edge cases)
- Asks for feedback on potential issues with the implementation

## Scenario 4: Code Optimization

### Best Practice: Specify Performance Bottlenecks and Ask for Fix

When you want a function optimized, it's important to identify where the performance issues are. Highlight the specific bottleneck or inefficiency and clarify what aspect of the performance you want to improve—whether it's speed, memory usage, or something else.

#### Formula for Code Optimization Prompts:

1. Provide context of your code: "I have a [type of code/function]"
2. Ask Q to identify potential performance issues and optimize the code: "Can you identify the potential performance issues and optimize the code?"
3. Provide code snippet: "Here is my code: [code]"

#### Example: Optimizing a Python Function for Speed

**Bad Prompt:**
```
Optimize this code:

def find_duplicates(numbers):
    duplicates = []
    for i in range(len(numbers)):
        for j in range(i + 1, len(numbers)):
            if numbers[i] == numbers[j] and numbers[i] not in duplicates:
                duplicates.append(numbers[i])
    return duplicates
```

**Why it's ineffective:**
- Doesn't specify what kind of optimization is needed
- Lacks context about the function's purpose
- No information about the typical input size or performance requirements

**Better Prompt:**
```
I have a Python function that finds duplicate values in a list of numbers. It works correctly, but it's very slow when processing large lists (over 10,000 items). I need to optimize it for better time complexity. Here's the code:

def find_duplicates(numbers):
    duplicates = []
    for i in range(len(numbers)):
        for j in range(i + 1, len(numbers)):
            if numbers[i] == numbers[j] and numbers[i] not in duplicates:
                duplicates.append(numbers[i])
    return duplicates

Can you identify the performance bottlenecks in this code and optimize it to handle large lists more efficiently? Please explain the time complexity of both the original and optimized versions.
```

**Why it's effective:**
- Clearly explains the function's purpose
- Specifies the performance issue (slow with large lists)
- Provides context about typical input size
- Requests explanation of time complexity for educational purposes

## Key Takeaways

| Scenario | Prompt Formula |
| ---------| -------------- |
| Debugging | Provide the Code & Context + Describe the Symptoms + Ask for Root Causes and Fix |
| Code Refactoring | Describe Code Issue + Specify Refactoring Goal + Provide Code Snippet |
| Unit Testing | Provide the Code + Request Unit Test Suggestions |
| Code Optimization | Provide the Context + Ask for Potential Performance Issues and Optimization + Provide Code Snippet |

By following these formulas and best practices, you can craft effective prompts for simple tasks that will yield more accurate and useful responses from Amazon Q Developer.

## Next Steps

Now that you've learned how to craft effective prompts for simple tasks, let's explore how Amazon Q understands your project context and how to leverage this understanding for more complex tasks.

---

[Next: Understanding Project Context](./03-project-context.md) | [Previous: Introduction to Prompt Engineering](./01-introduction.md) | [Back to Main](../README.md)
