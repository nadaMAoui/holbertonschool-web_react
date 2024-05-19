**# React State**

This document explores the fundamental concepts of state management in React, including component lifecycles, controlled components, forms, and state lifting. We'll also delve into React Hooks for enhanced functionality.

## Learning Objectives:

- **Component State:** Understanding how components manage internal data through the `state` property.
- **Component Lifecycle:** Grasping the key phases of a component's existence: mounting, updating, and unmounting.
- **State Modification:** Learning techniques to modify component state and trigger re-renders in a controlled manner.
- **Controlled Components:** Mastering form inputs where React manages the component's state based on user interactions.
- **React Forms:** Exploring how to create and handle form elements within React components.
- **Component Reusability and State Lifting:** Discovering how to break down complex components into smaller, reusable ones, and lifting shared state to appropriate containers.
- **React Hooks:** Understanding the introduction of Hooks in React v16.8, providing functional components with state and lifecycle methods.
- **Custom Hooks:** Learning how to create your own custom hooks to encapsulate reusable logic and state management patterns.
- **Testing State Changes:** Exploring methods for testing state updates in React components using Enzyme or other testing libraries.

## Component State and Lifecycle

**Component state** represents internal data that can change over time, triggering re-renders of the component and its children. Let's see how to define and modify state:

```javascript
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount(count + 1); // Update state using the setter function
  };

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={handleClick}>Click me</button>
    </div>
  );
}

export default Counter;
```

**Component lifecycle** refers to the different stages a component goes through during its existence:

- **Mounting:** When a component is first inserted into the DOM.
- **Updating:** When the component needs to re-render due to state or prop changes.
- **Unmounting:** When a component is removed from the DOM.

**State Modification:**

Here are some key principles for modifying state:

- **State updates are asynchronous:** Don't rely on the value of `state` immediately after updating it, as the update might happen later.
- **Use the state setter function** provided by `useState` to schedule state updates safely.
- **Avoid directly mutating state:** Always create a new state object with the desired changes.

## Controlled Components

Controlled components are form elements where React manages their state. The component's state reflects the current value of the input field.

```javascript
import React, { useState } from "react";

function NameForm() {
  const [name, setName] = useState("");

  const handleChange = (event) => {
    setName(event.target.value);
  };

  return (
    <div>
      <label>
        Name:
        <input type="text" value={name} onChange={handleChange} />
      </label>
      <p>Hello, {name}</p>
    </div>
  );
}

export default NameForm;
```

## React Forms

React forms handle user input through elements like `<input>`, `<textarea>`, `<select>`, etc. Here's an example with form submission:

```javascript
import React, { useState } from "react";

function ContactForm() {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");
  const [message, setMessage] = useState("");

  const handleSubmit = (event) => {
    event.preventDefault();
    // Form submission logic (e.g., send data to server)
    alert(`Name: ${name}, Email: ${email}, Message: ${message}`);
    setName("");
    setEmail("");
    setMessage("");
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input
          type="text"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
      </label>
      {/* Other input fields */}
      <button type="submit">Submit</button>
    </form>
  );
}

export default ContactForm;
```

## Component Reusability and State Lifting

to be finished >>
