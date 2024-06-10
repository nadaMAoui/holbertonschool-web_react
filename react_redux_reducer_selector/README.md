**# React Redux Reducer + Selector**

This project demonstrates the use of reducers and selectors in a React application powered by Redux for managing state.

**Learning Objectives:**

1. **Reducers: Purpose and Role**

   - Reducers are pure functions that handle state updates based on dispatched actions.
   - They receive the current state and an action as arguments.
   - They return a new state object, reflecting the state change caused by the action.

   ```javascript
   // Reducer function
   const initialState = { users: [] }; // Initial application state

   function usersReducer(state = initialState, action) {
     switch (action.type) {
       case "FETCH_USERS":
         return { ...state, loading: true }; // Update loading state
       case "USERS_RECEIVED":
         return { ...state, loading: false, users: action.payload }; // Update fetched users
       default:
         return state; // Return the current state for unknown actions
     }
   }
   ```

2. **Reducer Purity**

   - Reducers should be pure functions, meaning they:
     - Don't modify existing state objects directly (use object spread syntax `...state` for immutability).
     - Don't interact with external resources (like making API calls).
     - Rely solely on the provided state and action to determine the new state.

3. **Immutability with Immutable.js (Optional):**

   - Immutable.js is a library that enforces immutability by providing data structures that can't be directly modified.
   - Using it helps ensure reducer purity and avoid unintended state mutations.

   ```javascript
   // With Immutable.js
   import { Map } from "immutable";

   const initialState = Map({ users: [] });

   function usersReducer(state = initialState, action) {
     switch (action.type) {
       case "FETCH_USERS":
         return state.set("loading", true); // Update loading state immutably
       case "USERS_RECEIVED":
         return state.merge({ loading: false, users: action.payload }); // Update fetched users immutably
       default:
         return state;
     }
   }
   ```

4. **Normalizr (Optional):**

   - Normalizr is a library for normalizing nested API responses into a flat structure.
   - It helps reduce redundancy and simplify state management in complex applications.
   - Consider using it for managing deeply nested state structures.

5. **Selectors: Purpose and Usage**

   - Selectors are functions that extract specific data from the Redux store's global state.
   - They improve component decoupling by preventing components from needing to access the entire state directly.
   - Selectors can perform simple logic or data transformations before returning the selected value.

   ```javascript
   // Selector for retrieving all users
   const getAllUsers = (state) => state.usersReducer.users;

   // Selector for retrieving a specific user by ID
   const getUserById = (state, userId) => {
     const allUsers = getAllUsers(state);
     return allUsers.find((user) => user.id === userId);
   };
   ```

6. **Benefits of Selectors**
   - Selectors promote better component organization by hiding state access logic.
   - They make testing components easier by isolating the logic used to extract data from the state.
   - They allow for memoization, meaning the results are cached if the state hasn't changed, improving performance.

**Conclusion**

Reducers and selectors are fundamental concepts for managing state in React applications using Redux. By keeping reducers pure and using selectors for data retrieval, you can create a more maintainable, testable, and performant Redux application.
