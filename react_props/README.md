**# React Props**

## Learning Objectives

- **Functional Components:** Understand how to create basic React components using JavaScript functions.
- **Component Reuse:** Explore how to leverage components for efficient UI construction.
- **Passing Props:** Discover how to pass data (properties) from parent to child components.
- **Component Typing (Optional):** Learn about using TypeScript (or similar typing systems) to enhance code clarity and safety.
- **Fragments:** Understand the purpose and usage of React Fragments for concise JSX syntax.
- **Keys in Loops:** Grasp the importance of using keys when rendering lists to improve performance.

## Code Examples

**1. Functional Components**

```javascript
import React from "react";

function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

export default Greeting;
```

This component, `Greeting`, takes a prop named `name` and dynamically integrates it into the rendered heading.

**2. Component Reuse**

```javascript
import React from "react";
import Greeting from "./Greeting"; // Assuming Greeting component is in a separate file

function App() {
  return (
    <div>
      <Greeting name="Alice" />
      <Greeting name="Bob" />
    </div>
  );
}

export default App;
```

Here, the `App` component utilizes the `Greeting` component twice, passing different values for the `name` prop to achieve customized greetings.

**3. Passing Props**

We've already seen prop usage in the first example. Here's another demonstration:

```javascript
import React from "react";

function Profile(props) {
  return (
    <div>
      <h2>{props.fullName}</h2>
      <p>Age: {props.age}</p>
    </div>
  );
}

export default Profile;
```

The `Profile` component accepts `fullName` and `age` props for displaying profile information.

**4. Component Typing (Optional - TypeScript Example)**

```typescript
import React from "react";

interface User {
  name: string;
  age: number;
}

function Profile(props: User) {
  // Define props type as User interface
  return (
    <div>
      <h2>{props.name}</h2>
      <p>Age: {props.age}</p>
    </div>
  );
}

export default Profile;
```

In this example using TypeScript, we define an interface named `User` that specifies the expected types for the `name` and `age` props, enhancing code readability and catching potential errors during development.

**5. Fragments**

While not strictly necessary for prop usage, fragments provide a cleaner way to return multiple JSX elements from a component without introducing unnecessary extra divs:

```javascript
import React from "react";

function InfoCard() {
  return (
    <>
      {" "}
      {/* Fragment */}
      <h2>Product Details</h2>
      <p>Name: Acme Gadget</p>
      <p>Price: $19.99</p>
    </>
  );
}

export default InfoCard;
```

**6. Keys in Loops**

When rendering lists or elements that change order dynamically, it's crucial to provide a unique `key` prop to each element. This helps React efficiently update the UI by identifying which elements have changed, added, or removed, leading to better performance.

```javascript
import React from "react";

function Products() {
  const items = [
    { id: 1, name: "Item 1" },
    { id: 2, name: "Item 2" },
    { id: 3, name: "Item 3" },
  ];

  return (
    <ul>
      {items.map((item) => (
        <li key={item.id}>
          {" "}
          {/* Key prop based on unique ID */}
          {item.name}
        </li>
      ))}
    </ul>
  );
}

export default Products;
```

By providing a unique `key` prop based on the `id` property, React can efficiently update the list if items are added, removed, or reordered.
