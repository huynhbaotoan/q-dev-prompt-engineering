# Advanced Prompt Techniques

## Advanced Techniques

### 1. Provide Examples
- Include sample inputs and expected outputs
- Show existing code patterns you want to follow

### 2. Request Alternative Approaches
- Ask for multiple solutions to the same problem
- Request pros and cons of different approaches

### 3. Specify Output Format
- Request specific documentation styles (JSDoc, docstrings)
- Ask for comments at specific detail levels

### 4. Use System Design Patterns
- Reference known design patterns when appropriate
- Specify architectural constraints

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

- **Start broad, then narrow**: Begin with general questions, then refine
- **Build on previous responses**: Reference earlier parts of the conversation
- **Request modifications**: Ask for specific changes to generated code

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

```
I need to implement [specific functionality] in [language/framework].
Context:
- Project uses [relevant technologies/libraries]
- Must be compatible with [version/environment]
- Should follow [specific pattern/standard]

Requirements:
1. [First requirement]
2. [Second requirement]
3. [Third requirement]

Please provide a solution with appropriate error handling and comments.
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

```
Please review this [language] code for:
1. Performance issues
2. Security vulnerabilities
3. Best practice violations
4. Readability improvements

Code:
[paste code here]

Our environment uses [relevant context about deployment, scale, etc.]
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

```
I'm designing a system that needs to [business requirement].

Technical constraints:
- Expected traffic: [volume]
- Data storage needs: [size/requirements]
- Latency requirements: [specifics]
- Security requirements: [specifics]

I'm considering [approach A] or [approach B].
What AWS architecture would you recommend and why?
```

## AWS-Specific Best Practices

### 1. Service-Specific Context
- Mention which AWS services you're working with
- Specify service versions or features when relevant
- Include region information if it affects functionality

### 2. Infrastructure as Code
- Specify which IaC tool you're using (CloudFormation, CDK, Terraform)
- Mention deployment constraints or requirements
- Include existing resource patterns you want to follow

### 3. Security and Compliance
- Mention any specific security requirements
- Specify compliance frameworks that must be adhered to
- Ask for least-privilege IAM policy recommendations

---

[Next: Writing Effective Prompts for Complex Tasks](./05-complex-tasks.md) | [Previous: Understanding Project Context](./03-project-context.md) | [Back to Main](./README.md)
