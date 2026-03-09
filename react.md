# React Fundamentals Before Learning Next.js

This document summarizes the **core React concepts** you should understand before starting a project with Next.js.

Next.js is built on top of React, so understanding these fundamentals will make working with Next.js much easier.

---

# 1. JSX

JSX (JavaScript XML) is the syntax used by React to describe UI.

It looks similar to HTML but is actually **JavaScript that returns UI elements**.

Example:

```javascript
function App() {
  return (
    <div>
      <h1>Hello React</h1>
      <p>Welcome to my application</p>
    </div>
  );
}
```

Important rules:

- Only **one parent element** must be returned

- Use **className instead of class**

- JavaScript expressions must be inside `{}`

Example:

```javascript
const name = "David";

<h1>Hello {name}</h1>
```

---

# 2. Virtual DOM

React uses a **Virtual DOM (VDOM)** to optimize UI updates.

Process:

1. React renders JSX

2. React creates a **Virtual DOM representation**

3. When state changes, React creates a **new Virtual DOM**

4. React compares the **new VDOM with the previous VDOM** (diffing)

5. Only the **necessary parts of the real DOM are updated**

This process improves performance.

---

# 3. Rendering Behavior

When a component re-renders:

- The component function executes again

- **All its child components re-render by default**

Example:

```javascript
function Parent() {
  const [count, setCount] = useState(0);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>Click</button>
      <Child />
    </>
  );
}
```

Even if `Child` does not depend on `count`, it will re-render.

Ways to avoid unnecessary re-renders:

- Split components

- Use `React.memo`

- Use `useCallback`

- Use `useMemo`

---

# 4. React Hooks

Hooks allow functional components to use **state and lifecycle features**.

Common hooks:

- `useState`

- `useEffect`

- `useMemo`

- `useCallback`

- `useRef`

- `useContext`

Example:

```javascript
const [count, setCount] = useState(0);
```

---

# 5. Custom Hooks

You can create reusable logic using **custom hooks**.

Example:

```javascript
function useToggle(initialValue = false) {
  const [value, setValue] = useState(initialValue);

  const toggle = () => setValue(v => !v);

  return [value, toggle];
}
```

Usage:

```javascript
const [checked, toggleCheck] = useToggle();
```

Useful libraries for ready hooks:

- [https://usehooks-ts.com](https://usehooks-ts.com)

---

# 6. useCallback

`useCallback` is used to **memoize functions**.

Why?

Every render creates a **new function reference**, which can cause unnecessary re-renders in child components.

Example without optimization:

```javascript
function Parent() {
  const handleClick = () => console.log("clicked");

  return <Child onClick={handleClick} />;
}
```

React sees a **new function every render**.

Optimized version:

```javascript
const handleClick = useCallback(() => {
  console.log("clicked");
}, []);
```

Use it when:

- Passing functions to child components

- Preventing unnecessary renders

---

# 7. useMemo

`useMemo` memoizes **computed values**.

Useful for **expensive calculations**.

Example:

```javascript
const expensiveValue = useMemo(() => {
  return heavyCalculation(data);
}, [data]);
```

React recalculates **only when dependencies change**.

---

# 8. React.memo

`React.memo` prevents unnecessary re-rendering of components.

Example:

```javascript
const Child = React.memo(function Child({ value }) {
  console.log("render child");
  return <div>{value}</div>;
});
```

The component will **only re-render when props change**.

---

# 9. Portals

Portals allow you to **render elements in another part of the DOM tree**.

Common use cases:

- Modals

- Notifications

- Tooltips

Example:

```javascript
import { createPortal } from "react-dom";

function Modal({ children }) {
  return createPortal(
    <div className="modal">{children}</div>,
    document.body
  );
}
```

This **teleports the component** outside its normal hierarchy.

---

# 10. Error Boundaries

Error Boundaries catch **JavaScript errors in the component tree**.

Without them, an error can crash the whole React application.

Example:

```javascript
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }

    return this.props.children;
  }
}
```

Usage:

```javascript
<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>
```

---

# 11. Component Composition

React applications should be built using **small reusable components**.

Example:

Bad:

```textile
BigComponent
```

Better:

```ts
Header
Sidebar
Content
Footer
```

---

# 12. State vs Props

Props:

- Passed from parent to child

- Read-only

Example:

```js
<Child name="David" />
```

State:

- Managed inside a component

- Can change over time

Example:

```js
const [count, setCount] = useState(0);
```

---

# 13. Conditional Rendering

React allows rendering UI based on conditions.

Example:

```js
{isLoggedIn ? <Dashboard /> : <Login />}
```

---

# 14. List Rendering

Lists are rendered using `map()`.

Example

```js
users.map(user => (
  <User key={user.id} name={user.name} />
))
```

Always use **unique keys**.

---

# 15. Controlled Components (Forms)

React forms usually use **controlled inputs**.

Example:

```javascript
const [email, setEmail] = useState("");

<input
  value={email}
  onChange={(e) => setEmail(e.target.value)}
/>
```

---

# 16. Context API

Used for **global state sharing**.

Example:

```javascript
const AuthContext = createContext();
```

Useful for:

- Authentication

- Themes

- Global settings

---

# React Knowledge Required Before Next.js

You should be comfortable with:

- JSX

- Components

- Props / State

- Hooks

- Rendering behavior

- useCallback / useMemo

- React.memo

- Context API

- Forms

- Lists and conditional rendering

- Error boundaries

- Portals

Once these are understood, learning **Next.js becomes much easier**.
