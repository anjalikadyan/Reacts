React.js

A JavaScript library for building user interfaces.

Developed and maintained by Meta Platforms. React emphasizes reusable, composable components, declarative UIs, and efficient updates via the Virtual DOM.

Key Features

- Component-based architecture
- Declarative UI
- One-way data flow (top-down data via props)
- Fast rendering using Virtual DOM
- Large ecosystem and community support

Getting Started

- Prerequisites: Node.js (LTS) and npm or yarn.
- Create a project:

```bash
npm create vite@latest my-app -- --template react
cd my-app
npm install
npm run dev
```

Core Concepts

Components

- Function Components (preferred):

```jsx
function Welcome() {
  return <h1>Hello, React!</h1>;
}
```

- Class Components (legacy but useful to recognize):

```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, React!</h1>;
  }
}
```

JSX Basics

- JSX lets you write HTML-like syntax in JavaScript.
- Wrap multiple elements in a single parent (e.g., a fragment `<>...</>`).
- Use `{}` to embed JavaScript expressions.

Props (Properties)

- Pass data from parent to child; props are read-only.

```jsx
function Greeting({ name }) {
  return <h2>Hello, {name}!</h2>;
}

// Usage
<Greeting name="Anjali" />
```

State

- Local, mutable data managed within a component.

```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

Handling Events

- Use camelCase event names and pass a function reference.

```jsx
function Button() {
  function handleClick() {
    console.log('Clicked');
  }
  return <button onClick={handleClick}>Click me</button>;
}
```

Conditional Rendering

```jsx
function Status({ isOnline }) {
  return <span>{isOnline ? 'Online' : 'Offline'}</span>;
}
```

Lists and Keys

- Use `key` to help React identify list items.

```jsx
const users = [
  { id: 1, name: 'Ava' },
  { id: 2, name: 'Ben' }
];

function UserList() {
  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

Styling in React

- Inline styles:

```jsx
<h1 style={{ color: 'blue' }}>Hello</h1>
```

- External CSS:

```jsx
import './App.css';
```

- Scoped styling:
  - CSS Modules: `import styles from './Button.module.css'`
  - Styled Components: `npm install styled-components`

Hooks (Functional Components)

- `useState` — local state
- `useEffect` — side effects (fetching, subscriptions)
- `useMemo` — memoize expensive computations
- `useCallback` — memoize functions to avoid re-renders
- `useRef` — mutable refs and DOM access

```jsx
import { useEffect, useState } from 'react';

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    async function load() {
      const res = await fetch('https://jsonplaceholder.typicode.com/users');
      setUsers(await res.json());
    }
    load();
  }, []); // runs once after mount

  return <div>Total users: {users.length}</div>;
}
```

Lifecycle (Class vs Hooks)

- Class: `componentDidMount`, `componentDidUpdate`, `componentWillUnmount`.
- Hooks: `useEffect` with appropriate dependency arrays to model lifecycle.

Routing (Basics)

```bash
npm install react-router-dom
```

```jsx
import { BrowserRouter, Routes, Route, Link } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link>
      </nav>
      <Routes>
        <Route path="/" element={<h1>Home</h1>} />
        <Route path="/about" element={<h1>About</h1>} />
      </Routes>
    </BrowserRouter>
  );
}
```

Forms (Controlled Inputs)

```jsx
import { useState } from 'react';

function NameForm() {
  const [name, setName] = useState('');
  function handleSubmit(e) {
    e.preventDefault();
    alert(name);
  }
  return (
    <form onSubmit={handleSubmit}>
      <input value={name} onChange={e => setName(e.target.value)} />
      <button type="submit">Submit</button>
    </form>
  );
}
```

Performance Tips

- Split components and keep state minimal.
- Use `React.memo` for pure child components.
- Memoize expensive work with `useMemo` and handlers with `useCallback`.
- Virtualize long lists (`react-window`, `react-virtualized`).

Testing (Basics)

```bash
npm install --save-dev @testing-library/react @testing-library/jest-dom
```

```jsx
import { render, screen } from '@testing-library/react';
import '@testing-library/jest-dom';

test('renders greeting', () => {
  render(<h1>Hello</h1>);
  expect(screen.getByText('Hello')).toBeInTheDocument();
});
```

Further Reading

- Official Docs: `https://react.dev`
- React Router: `https://reactrouter.com`
- Styled Components: `https://styled-components.com`
