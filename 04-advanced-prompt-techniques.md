# Advanced Prompt Techniques

## Chain of Thought Prompting

Guide Amazon Q through a step-by-step reasoning process for complex problems.

**Example**: "I need to optimize a slow-performing Lambda function. Let's approach this systematically:
1. First, help me identify potential bottlenecks in my code
2. Then, suggest specific optimizations for each bottleneck
3. Finally, provide a refactored version of the function with these optimizations"

## Iterative Refinement

Start with a basic prompt and refine it based on the responses.

**Initial prompt**: "Help me create an S3 bucket using CloudFormation."  
**Refinement**: "Thanks. Now add versioning and encryption to this S3 bucket template."  
**Further refinement**: "Great. Can you modify the template to include lifecycle rules that transition objects to Glacier after 90 days?"

## Comparative Analysis

Ask Amazon Q to compare different approaches.

**Example**: "Compare and contrast using AWS Lambda versus Amazon ECS for running a microservice that processes data every 15 minutes. Consider factors like cost, scalability, maintenance overhead, and cold start times."

## Role-Based Prompting

Assign a specific role to Amazon Q to get specialized responses.

**Example**: "As a security expert, review my IAM policy and suggest improvements to follow the principle of least privilege."

**Example**: "As a database architect, help me optimize this DynamoDB query for better performance."

## Built-in Agent Experiences

Amazon Q offers specialized agent experiences through slash commands:

- **/dev**: For general development assistance
- **/test**: For testing-related tasks
- **/docs**: For documentation help
- **/review**: For code review assistance

**Example**: "/test Generate unit tests for this function using pytest."

## Task-Specific Prompt Templates

### Code Generation

```
I need to implement [specific functionality] in [language].
Requirements:
- [requirement 1]
- [requirement 2]
- [requirement 3]
Technical constraints:
- [constraint 1]
- [constraint 2]
Please provide a complete implementation with error handling and comments.
```

### Code Review

```
Please review the following code in @[filename]:
Focus on:
- Security issues
- Performance optimizations
- Best practices
- Readability and maintainability
```

### Debugging

```
I'm encountering the following error:
[error message]

Here's the relevant code:
@[filename]

What might be causing this issue and how can I fix it?
```

### Architecture Design

```
I need to design a [type of system] for [specific use case].
Requirements:
- [requirement 1]
- [requirement 2]
- [requirement 3]
Constraints:
- [constraint 1]
- [constraint 2]
Please suggest an AWS architecture with justifications for each component choice.
```

---

[Next: Writing Effective Prompts for Complex Tasks](./05-complex-tasks.md) | [Previous: Crafting Effective Prompts for Simple Tasks](./03-project-context.md) | [Back to Main](./README.md)
