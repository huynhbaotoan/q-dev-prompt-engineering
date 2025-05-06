# Writing Effective Prompts for Complex Tasks

Now that you understand how Amazon Q Developer builds context from your project, it's time to learn how to guide it through complex tasks. By breaking down complex tasks into smaller, distinct functions or methods, you enable Amazon Q to better understand and execute your instructions.

## Chain-of-Thought (CoT) Prompting

Chain-of-thought (CoT) prompting is a technique that guides large language models like Amazon Q Developer to think step-by-step through a task instead of jumping straight to the final result.

### What is Chain-of-Thought Prompting?

Chain-of-thought prompting generates a sequence of short and actionable prompts to describe reasoning logics step by step, known as reasoning chains or rationales, to eventually lead to the final answer/output.

**Analogy:** Imagine you're asking a chef to make a pizza for you. If you simply say, `make me a pizza,` they might miss some details or make choices you wouldn't expect. They'll probably use a sauce you don't prefer or bake it too long. In coding, simply asking for a "pizza" is like asking Amazon Q to complete a complex coding task with minimal instruction.

Guide Amazon Q through a step-by-step reasoning process for complex problems.

**Example**: "I need to optimize a slow-performing Lambda function. Let's approach this systematically:
1. First, help me identify potential bottlenecks in my code
2. Then, suggest specific optimizations for each bottleneck
3. Finally, provide a refactored version of the function with these optimizations"

### Why is CoT Useful?

Studies have shown that chain-of-thought prompting significantly improves a model's performance on tasks requiring high levels of logic, such as:
- Arithmetic
- Common sense reasoning
- Symbolic reasoning
- Complex coding tasks

In software development, completing a complex coding task requires clear and structured logic. By guiding Amazon Q to generate complex coding tasks in a logical sequence, much like how a developer would approach solutions, we can reduce errors and improve code quality.

## Chain-of-Thought Best Practices

Let's use a case study to demonstrate CoT best practices that guide your prompts step-by-step for clear, accurate results.

### Scenario: Filtering User Data

You are tasked with writing a function that filters user data to find users who meet certain conditions.

#### 1. Break Down Your Main Task into Subtasks

First, start by thinking about the main goal of your task. Then think about the main subtasks needed to achieve the goal.

You can also ask Amazon Q to break down your main task into subtasks, and refine any subtask as needed:

**Prompt to Amazon Q:**
```
I'm writing a function that filters user data to find users who meet certain conditions. Let's first think step-by-step. What are the main subtasks needed to achieve this?
```

**Example Response:**
```
To create a function that filters user data based on specific conditions, we can break this down into these subtasks:

1. Define the data input and storage: Determine how user data will be structured and accessed
2. Specify the filtering conditions: Define the criteria that users must meet
3. Implement the filtering logic: Write the code that applies the conditions to the data
4. Handle edge cases: Account for empty datasets, missing fields, or invalid inputs
5. Optimize for performance: Ensure the function works efficiently with large datasets
6. Return the filtered results: Format and return the matching users

Would you like me to help you implement any specific subtask?
```

#### 2. Start a Subtask with a Limited Scope

If every subtask looks correct, you can start with the first subtask, focusing on a limited scope first. Provide detailed instructions to help Amazon Q generate a basic output initially:

**Prompt to Amazon Q:**
```
Now I want to write the first subtask: Define the data input and storage. Please determine the appropriate data structure to store user information, suggest how to load this data from sources like files or memory, and validate the input format to ensure consistency. Provide an initial implementation in Java based on this information.
```

#### 3. Refine the Output

Next, refine the output to better meet your needs by providing more specific instructions. If you're unsure about the exact requirements, you can ask Amazon Q to first identify the areas that can be improved and explain why:

**Prompt:**
```
What aspects of your code could be improved? Please list the areas that can be refined or optimized and explain why.
```

Then, pick the use cases that align with your situation and provide more details to help Amazon Q enhance the output further:

**Prompt Example:**
```
For performance optimization, how would you optimize this function for large datasets, potentially with millions of users?
```

Next, select the approaches that apply to your situation, and then ask Amazon Q to generate a complete code:

**Prompt Example:**
```
Please generate a complete code using approach 1, 2, and 3.
```

#### 4. Build on Previous Output

After successfully completing a step/subtask, use the previous output as the foundation for the next step/subtask. Reference the earlier work directly so the model stays consistent with previous prompts:

**Prompt Example:**
```
My service is latency sensitive. Based on this output, please optimize the code for time complexity improvement.
```

#### 5. Review and Iterate

Last but not least, carefully review Amazon Q's full responses to ensure it meets your requirements. Identify any steps or details that may need clarification or adjustment. If necessary, go back to previous prompts and refine them to improve overall flow and accuracy. Repeat this process until you achieve the desired result.

## Example: Complete Chain-of-Thought Workflow

Let's see a complete example of using chain-of-thought prompting to implement a user data filtering function:

### Step 1: Break Down the Task

**Prompt:**
```
I need to implement a function that filters a list of users based on multiple criteria like age, location, and subscription status. Let's break this down into steps. What would be the logical steps to implement this functionality?
```

### Step 2: Define Data Structure

**Prompt:**
```
Great breakdown. Let's start with defining the User class in Java. The User should have the following properties: id, name, age, location, subscriptionStatus (which can be BASIC, PREMIUM, or ENTERPRISE), and registrationDate. Please implement this class with appropriate getters, setters, and a builder pattern for easy instantiation.
```

### Step 3: Implement Filtering Logic

**Prompt:**
```
Now, let's implement the filtering logic. I need a UserFilter class that can:
1. Filter users by minimum and maximum age
2. Filter users by location (exact match)
3. Filter users by subscription status
4. Filter users by registration date range
5. Allow chaining these filters together

Please implement this class using a fluent interface design pattern.
```

### Step 4: Add Performance Optimization

**Prompt:**
```
The UserFilter implementation looks good, but I'm concerned about performance with large datasets. Can you optimize it to:
1. Use streams efficiently
2. Implement lazy evaluation where possible
3. Add parallel processing capability for large datasets
4. Include a method to estimate if parallel processing would be beneficial based on the dataset size
```

### Step 5: Handle Edge Cases

**Prompt:**
```
Now let's make the filter more robust by handling these edge cases:
1. Null values in user properties
2. Empty filter criteria (should match all users)
3. Invalid filter criteria (e.g., negative age)
4. Empty user list

Please update the implementation to handle these cases gracefully.
```

### Step 6: Add Documentation and Examples

**Prompt:**
```
Finally, please add comprehensive JavaDoc documentation to all classes and methods, and provide a complete example showing how to use the UserFilter with a sample dataset of users.
```

By following this chain-of-thought approach, you guide Amazon Q Developer through a logical progression of steps, resulting in a more complete, accurate, and well-designed solution than if you had requested the entire implementation at once.

## Next Steps

Now that you've learned how to use chain-of-thought prompting for complex tasks, let's explore techniques for reducing hallucinations and inaccuracies in Amazon Q Developer's responses.

---

[Next: Reducing Hallucinations and Inaccuracies](./06-reducing-hallucinations.md) | [Previous: Understanding Project Context](./04-advanced-prompt-techniques.md) | [Back to Main](./README.md)
