# Practical Exercises

Now that you've learned the principles and techniques of prompt engineering for Amazon Q Developer, it's time to put your knowledge into practice. This section provides a series of exercises designed to help you apply what you've learned in real-world scenarios.

## Example 1: Implementing a Feature

```
I need to implement a user authentication system for a Flask application.

Requirements:
- Support email/password login
- Include password reset functionality
- Implement JWT-based session management
- Follow security best practices

Here's my current project structure:
@app.py
@models/user.py
@routes/

Please provide the necessary code changes and explain your implementation approach.
```

## Example 2: Debugging an Issue

```
I'm getting the following error when trying to deploy my CloudFormation stack:

"Resource of type 'AWS::IAM::Role' with identifier 'LambdaExecutionRole' already exists."

Here's my template:
@cloudformation/template.yaml

What's causing this error and how can I fix it?
```

## Example 3: Architecture Review

```
As a cloud architect, please review my serverless architecture for a high-traffic e-commerce application:
@architecture/diagram.md
@architecture/requirements.md

Specifically, I'm concerned about:
1. Scalability during flash sales
2. Cost optimization
3. Resilience to regional outages
4. Data consistency across services

Suggest improvements and identify any potential issues.
```

## Example 4: Code Optimization

```
Using @workspace, analyze my Lambda function that processes large S3 files. It's currently taking too long to execute and sometimes times out.

Please identify performance bottlenecks and suggest optimizations to:
1. Reduce execution time
2. Lower memory usage
3. Improve error handling
4. Make the code more maintainable

Provide specific code changes with explanations.
```

## Example 5: Learning a New Concept

```
Explain AWS Step Functions to me as if I'm an experienced developer but new to workflow orchestration.

Include:
- Core concepts and terminology
- When to use Step Functions vs. other AWS services
- Best practices for error handling and retries
- A simple example of a Step Function definition for an order processing workflow
- Common pitfalls to avoid
```

## Exercise 6: Improving Basic Prompts

**Objective:** Practice transforming vague prompts into effective ones using the C.R.I.S.P. framework.

**Instructions:**

For each of the following vague prompts, rewrite them to be more effective using the C.R.I.S.P. framework:

1. "Fix this code."
2. "Write a function to process data."
3. "Make this code more efficient."
4. "Create a login system."
5. "Help me with error handling."

**Example Solution for #1:**

Vague prompt: "Fix this code."

Improved prompt:
```
I have a JavaScript function that's supposed to calculate the average of numbers in an array, but it's returning NaN when the array is empty. Here's the code:

function calculateAverage(numbers) {
  let sum = 0;
  for (let i = 0; i < numbers.length; i++) {
    sum += numbers[i];
  }
  return sum / numbers.length;
}

Please fix this function to handle empty arrays by returning 0 instead of NaN. Also, check if there are any other edge cases that should be handled, such as non-numeric values in the array.
```

This improved prompt:
- Provides clear context about what the code does
- Specifies the exact issue (returning NaN for empty arrays)
- Includes the complete code snippet
- Specifies the desired behavior for edge cases
- Asks for consideration of additional edge cases

## Exercise 7: Debugging with Effective Prompts

**Objective:** Practice creating effective debugging prompts that provide sufficient context and information.

**Instructions:**

Imagine you're encountering the following errors in your code. Write effective prompts for Amazon Q Developer to help you debug each issue:

1. A React component that's re-rendering infinitely
2. A Python function that's throwing a "KeyError" exception
3. A Java method that's causing a memory leak
4. A Node.js API endpoint that's returning 500 errors intermittently
5. A CSS layout that's breaking on mobile devices

**Example Solution for #1:**

```
I have a React functional component that's causing infinite re-renders. Here's the component code:

function UserProfile({ userId }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  
  useEffect(() => {
    async function fetchUser() {
      setLoading(true);
      try {
        const response = await fetch(`/api/users/${userId}`);
        const data = await response.json();
        setUser(data);
      } catch (error) {
        console.error('Error fetching user:', error);
      } finally {
        setLoading(false);
      }
    }
    
    fetchUser();
  });
  
  if (loading) return <div>Loading...</div>;
  if (!user) return <div>User not found</div>;
  
  return (
    <div className="user-profile">
      <h1>{user.name}</h1>
      <p>Email: {user.email}</p>
      <p>Role: {user.role}</p>
    </div>
  );
}

The component is causing the browser to freeze due to infinite re-renders. I've verified that the API endpoint works correctly and returns the expected data. What's causing the infinite re-renders and how can I fix it?
```

## Exercise 8: Refactoring with Chain-of-Thought Prompting

**Objective:** Practice using chain-of-thought prompting to guide Amazon Q through a complex refactoring task.

**Instructions:**

You have a complex function that needs refactoring. Create a series of prompts that guide Amazon Q Developer through the refactoring process step by step.

**Starting Code:**
```javascript
function processOrderData(orders) {
  let totalRevenue = 0;
  let highValueOrders = [];
  let customerFrequency = {};
  let productPopularity = {};
  let monthlyRevenue = {
    'Jan': 0, 'Feb': 0, 'Mar': 0, 'Apr': 0, 'May': 0, 'Jun': 0,
    'Jul': 0, 'Aug': 0, 'Sep': 0, 'Oct': 0, 'Nov': 0, 'Dec': 0
  };
  
  for (let i = 0; i < orders.length; i++) {
    const order = orders[i];
    totalRevenue += order.total;
    
    if (order.total > 1000) {
      highValueOrders.push(order);
    }
    
    if (customerFrequency[order.customerId]) {
      customerFrequency[order.customerId]++;
    } else {
      customerFrequency[order.customerId] = 1;
    }
    
    const orderDate = new Date(order.date);
    const month = orderDate.toLocaleString('en-US', { month: 'short' });
    monthlyRevenue[month] += order.total;
    
    for (let j = 0; j < order.items.length; j++) {
      const item = order.items[j];
      if (productPopularity[item.productId]) {
        productPopularity[item.productId] += item.quantity;
      } else {
        productPopularity[item.productId] = item.quantity;
      }
    }
  }
  
  let topCustomers = [];
  for (const customerId in customerFrequency) {
    topCustomers.push({ customerId, frequency: customerFrequency[customerId] });
  }
  topCustomers.sort((a, b) => b.frequency - a.frequency);
  topCustomers = topCustomers.slice(0, 10);
  
  let topProducts = [];
  for (const productId in productPopularity) {
    topProducts.push({ productId, quantity: productPopularity[productId] });
  }
  topProducts.sort((a, b) => b.quantity - a.quantity);
  topProducts = topProducts.slice(0, 10);
  
  return {
    totalRevenue,
    highValueOrders,
    topCustomers,
    topProducts,
    monthlyRevenue
  };
}
```

**Example Chain of Prompts:**

1. First prompt:
```
I have a JavaScript function that processes order data and calculates various metrics. The function works but it's becoming hard to maintain as we add more metrics. I'd like to refactor it to be more modular and maintainable. Let's start by analyzing the current function to identify its responsibilities and potential areas for improvement. Here's the function:

[Insert the function code here]

Can you analyze this function and identify its main responsibilities and any code smells or areas for improvement?
```

2. Second prompt (after receiving the analysis):
```
Thank you for the analysis. Now, let's break down this function into smaller, more focused functions. Can you suggest a modular structure where each function has a single responsibility? Please provide a high-level outline of the functions we should create.
```

3. Third prompt (after receiving the modular structure):
```
That structure looks good. Let's start implementing the refactored code. Can you implement the first two functions: one for calculating total revenue and another for identifying high-value orders?
```

4. Continue with similar prompts for each module until the entire function is refactored.

## Exercise 9: Handling Potential Hallucinations

**Objective:** Practice techniques for identifying and reducing hallucinations in Amazon Q Developer's responses.

**Instructions:**

For each of the following scenarios, write a prompt that includes techniques to reduce the risk of hallucinations:

1. Asking about a specific AWS service configuration
2. Requesting information about a programming language feature
3. Asking for best practices in a specific domain
4. Requesting an implementation of a complex algorithm
5. Asking about compatibility between different libraries or frameworks

**Example Solution for #1:**

```
I need to configure an AWS Lambda function to connect to an RDS database in a VPC. Please provide step-by-step instructions for:

1. Creating the necessary IAM roles and policies
2. Configuring the VPC settings for the Lambda function
3. Setting up security groups to allow the Lambda function to access the RDS instance
4. Handling connection pooling for efficient database access

For each step, please:
- Explain the purpose and importance
- Provide specific AWS CLI commands or console instructions
- Note any common pitfalls or security considerations

If you're uncertain about any specific detail, please indicate this rather than providing potentially incorrect information. Also, please cite any AWS documentation or best practices you're referencing.
```

This prompt:
- Breaks down the complex task into specific steps
- Asks for explanations along with instructions
- Explicitly gives permission to acknowledge uncertainty
- Requests citations for information sources

## Exercise 10: Complex Task Decomposition

**Objective:** Practice breaking down a complex task into smaller, manageable subtasks for Amazon Q Developer.

**Instructions:**

Choose one of the following complex tasks and create a series of prompts that break it down into smaller subtasks:

1. Building a full-stack web application for task management
2. Creating a data processing pipeline for large CSV files
3. Implementing a recommendation system based on user behavior
4. Developing a CI/CD pipeline for a microservices architecture
5. Building a real-time dashboard for monitoring system metrics

**Example Solution for #1:**

First prompt:
```
I want to build a full-stack task management web application with React for the frontend and Node.js/Express for the backend. Let's break this down into manageable components. What would be the main components and features needed for this application?
```

After receiving the breakdown, follow up with specific prompts for each component:

For the data model:
```
Let's start by designing the data models for the task management application. I need models for:
1. Users (with authentication)
2. Tasks (with title, description, due date, priority, status)
3. Projects (to group related tasks)
4. Tags (to categorize tasks)

Please design these models with appropriate fields, relationships, and validation rules. Use Mongoose schemas for MongoDB as the database.
```

For the backend API:
```
Now, let's implement the RESTful API endpoints for task management. Based on the data models we designed, I need endpoints for:
1. User authentication (register, login, logout)
2. CRUD operations for tasks
3. CRUD operations for projects
4. Adding/removing tags from tasks
5. Filtering and sorting tasks

Please implement these endpoints using Express.js with proper error handling, input validation, and authentication middleware.
```

Continue with similar focused prompts for each component of the application.

## Next Steps

Now that you've practiced applying prompt engineering techniques with these exercises, you're ready to use these skills in your real-world development tasks. Remember that effective prompt engineering is both an art and a science—it improves with practice and experimentation.

In the next section, we'll explore some advanced techniques and tips for getting the most out of Amazon Q Developer.

---

[Next: Advanced Tips and Techniques](./07-advanced-tips.md) | [Previous: Reducing Hallucinations and Inaccuracies](./05-reducing-hallucinations.md) | [Back to Main](../README.md)
