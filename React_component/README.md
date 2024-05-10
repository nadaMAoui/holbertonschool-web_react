**# Mastering React Components: Beyond the Basics**

Welcome to this guide that delves deeper into crafting robust, well-tested, and performant React components! Explore advanced concepts like class vs. functional components, lifecycle methods, component testing, higher-order components (HOCs), and performance optimization.

## Learning Objectives:

- **Choosing Your Weapon: Class vs. Function**
  - When to wield a class component for state management and lifecycle methods.
  - When to favor a functional component for simplicity and performance.
- **The Lifecycle of a React Class**
  - Understand the different stages a class component goes through (mount, update, unmount).
  - Leverage lifecycle methods like `componentDidMount` to fetch data or `componentWillUnmount` to clean up resources.
- **Testing, Testing, 1, 2, 3!**
  - Why you should write tests for your components to ensure reliability.
  - Discover how Jest helps you create effective unit tests.
- **Spying on Your Components with Jest Spies**
  - Learn how Jest spies allow you to verify if functions within your components are called as expected.
- **Higher-Order Components (HOCs) to the Rescue!**
  - Grasp the concept of HOCs and how they promote code reusability and separation of concerns.
- **Optimizing Performance: When to Render and When Not To**
  - Explore techniques to boost rendering performance, such as `React.memo` for conditional rendering and memoization.

## Code Examples:

Let's dive into some code snippets to illustrate these concepts:

**1. Class vs. Functional Component:**

```javascript
// Class component for managing state and lifecycle events
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  handleClick = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button onClick={this.handleClick}>Click me</button>
      </div>
    );
  }
}

// Functional component for simple display (no state needed)
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```

**2. Component Lifecycle (Using `componentDidMount`):**

```javascript
class NetworkDataFetcher extends React.Component {
  componentDidMount() {
    fetch("https://api.example.com/data")
      .then((response) => response.json())
      .then((data) => this.setState({ data }));
  }

  // ...

  render() {
    // ...
  }
}
```

**3. Component Testing with Jest (Simplified Example):**

```javascript
// Greeting.test.js (using Jest)
import React from "react";
import { render, screen } from "@testing-library/react";
import Greeting from "./Greeting"; // Assuming Greeting component exists

test("renders name correctly", () => {
  render(<Greeting name="Alice" />);
  const heading = screen.getByText(/Hello, Alice!/i); // Case-insensitive match
  expect(heading).toBeInTheDocument();
});
```

**4. Jest Spy Example:**

```javascript
// YourComponent.test.js
import React from "react";
import { render } from "@testing-library/react";
import YourComponent from "./YourComponent";

jest.mock("./SomeService"); // Mocking a service

test("calls SomeService on button click", () => {
  const mockSomeService = require("./SomeService"); // Access the mock

  render(<YourComponent />);
  const button = screen.getByRole("button");
  fireEvent.click(button);

  expect(mockSomeService.fetchData).toHaveBeenCalled(); // Verify function call
});
```

**5. Higher-Order Component (HOC) Example:**

```javascript
// withAuth.js (HOC to wrap components with authentication)
const withAuth = (WrappedComponent) => (props) => {
  const isAuthenticated = true; // Assuming authentication logic

  return isAuthenticated ? (
    <WrappedComponent {...props} />
  ) : (
    <p>Please Login</p>
  );
};

// SomeComponent wrapped with authentication
const AuthenticatedComponent = withAuth(SomeComponent);
```

**6. Performance Optimization with `React.memo`:**

```javascript
import React, {}
```
