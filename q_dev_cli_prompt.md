# Amazon Q Developer CLI: Prompt Engineering Guide

## CLI-Specific Considerations

### 1. Context Awareness
- The CLI has access to your local environment and files
- Be specific about which files or directories you want Q to analyze
- Reference file paths explicitly when asking about specific code

### 2. Command Structure
- Use clear, command-like language for best results
- Start with verbs that indicate your intent (analyze, explain, modify)
- Specify the scope of your request (this file, this function, this project)

### 3. Working with Local Files
- Specify relative or absolute paths when referring to files
- For multi-file operations, indicate relationships between files
- When asking for code modifications, specify exactly where changes should be made

## Effective CLI Prompts

### Code Analysis Example
```
"Analyze the error handling in ./src/utils/validation.js and suggest improvements"
```

### Project Understanding Example
```
"Explain how the authentication flow works across the files in ./src/auth/"
```

### Code Generation Example
```
"Create a unit test for the function in ./src/services/payment.js that handles refunds"
```

### Refactoring Example
```
"Refactor the error handling in ./app.js to use async/await instead of promises"
```

## CLI Environment Awareness

### 1. Project Structure
- Q CLI can understand your project structure, so reference it
- Ask about relationships between components in your codebase
- Use project-specific terminology that matches your file structure

### 2. Development Environment
- Mention relevant environment variables or configuration
- Specify runtime context (Node.js version, Python version, etc.)
- Reference package dependencies that might be relevant

### 3. Terminal Integration
- Q can suggest terminal commands relevant to your project
- Ask for help with build scripts, deployment commands, or debugging tools
- Request explanations of command output or error messages

## Best Practices for CLI Interaction

### 1. Progressive Refinement
- Start with broader questions about your codebase
- Narrow down to specific files or functions
- Use follow-up questions to drill deeper into specific issues

### 2. Contextual Continuity
- Reference previous commands or responses in follow-up questions
- Build on Q's understanding of your project over the conversation
- Use phrases like "in the file we just discussed" or "based on your last suggestion"

### 3. Explicit Boundaries
- Clearly indicate when you're switching context to a different part of your project
- Specify when you want Q to ignore certain files or directories
- Be clear about which version of a file you're referring to

## Advanced CLI Techniques

### 1. Combining File Operations with Questions
```
"After looking at ./src/api/endpoints.js, explain how the authentication middleware in ./src/middleware/auth.js is being applied"
```

### 2. Requesting Specific Output Formats
```
"Generate a JSON schema for the data structure in ./src/models/user.js"
```

### 3. Comparative Analysis
```
"Compare the error handling approaches in ./src/services/orders.js and ./src/services/payments.js and suggest a consistent pattern"
```

### 4. Incremental Code Generation
```
"First, create a basic Express route handler for user registration. Then, add input validation using Joi."
```

## Troubleshooting CLI Interactions

### 1. When Q Misunderstands Your Codebase
- Provide more explicit file paths
- Describe the purpose or functionality of files
- Share snippets of relevant code for context

### 2. When Responses Are Too General
- Ask for specific examples related to your code
- Request concrete implementation details
- Specify the level of detail you need

### 3. When Dealing with Complex Projects
- Break down requests into smaller, focused questions
- Establish context by describing the project architecture first
- Reference specific design patterns or architectural decisions

## Conclusion

Effective prompt engineering for Amazon Q Developer CLI leverages its unique ability to understand your local development environment. By being specific about file paths, project structure, and development context, you can get more precise and actionable responses that directly apply to your codebase.

Practice these techniques to improve your productivity with Amazon Q Developer CLI and make it an even more valuable part of your development workflow.
