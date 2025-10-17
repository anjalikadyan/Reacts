# React js

A JavaScript library for building user interfaces.
Developed and maintained by Meta Platforms.
Based on **component-based architecture**, making code reusable and easier to maintain.
Uses **Virtual DOM** for efficient UI updates.

---

### **Key Features:**

* Component-based
* Declarative UI
* One-way data binding
* Fast rendering using Virtual DOM
* Strong community support

---

## **Components:**

### Function Components: Simple and widely used.

```jsx
function Welcome() {
  return <h1>Hello, React!</h1>;
}

export default Welcome;
```

Usage:

```jsx
import Welcome from './Welcome';

function App() {
  return <Welcome />;
}
```

---

### Class Components: Less common today but good to know.

```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, React!</h1>;
  }
}

export default Welcome;
```

Usage:

```jsx
import Welcome from './Welcome';

function App() {
  return <Welcome />;
}
```

---

## **Props (Properties)**

* Used to pass data from parent to child component.

```jsx
function Greeting(props) {
  return <h2>Hello, {props.name}!</h2>;
}

export default Greeting;
```

Usage:

```jsx
import Greeting from './Greeting';

function App() {
  return (
    <div>
      <Greeting name="Anjali" />
      <Greeting name="Rahul" />
    </div>
  );
}
```

---

## **Styling in React:**

### Inline styling

```jsx
<h1 style={{ color: "blue", fontSize: "24px" }}>Hello</h1>
```

---

### External CSS

```jsx
import './App.css';

function App() {
  return <h1 className="title">Hello</h1>;
}
```

```css
/* App.css */
.title {
  color: red;
  text-align: center;
}
```

---

## **CSS Modules or Styled Components for scoped styling:**

### ✅ Use CSS Modules if you prefer separate CSS files.

```jsx
// Button.module.css
.btn {
  background-color: blue;
  color: white;
  padding: 10px;
  border: none;
}
```

```jsx
// Button.jsx
import styles from './Button.module.css';

function Button() {
  return <button className={styles.btn}>Click Me</button>;
}

export default Button;
```

---

### ✅ Use Styled Components if you like CSS inside JavaScript and want easy dynamic styles.

```bash
npm install styled-components
```

```jsx
import styled from 'styled-components';

const Button = styled.button`
  background-color: green;
  color: white;
  padding: 10px;
  border: none;
`;

function App() {
  return <Button>Click Me</Button>;
}

export default App;
```
# Routing in React

--it is allows your application to navigate between different components or pages without reloading the browser.  
--its make web app behave like a single-page application (SPA) - fast and smooth.

## Install React Router
```bash
npm install react-router-dom
````

## Example

```jsx
import { BrowserRouter, Routes, Route, Link } from 'react-router-dom';

function Home() {
  return <h1>Home Page</h1>;
}

function About() {
  return <h1>About Page</h1>;
}

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

## How it works

--`BrowserRouter` wraps the entire app to enable routing.
--`Link` is used to navigate between pages without reloading.
--`Routes` and `Route` tell React which component to show for each URL path.
--the page does not reload, only the content changes.

```



