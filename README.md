# 🥋 Frontend Onboarding Guide 🥋

#### Front-end Team Onboarding Guide for internship in WACOCO HQ

Welcome to the WACOCO **Front-end Team**! This guide will help you get started by walking you through the basics of setting up your environment and working on components, all while using the karate belt system to represent your progress. Each step should take about 5 minutes, and by the end of this guide, you'll be ready to dive into the real project.

## 🎯 Goal:

1. Set up a frontend project with **Vite** and **Storybook**.
2. Create and document components in **Storybook**.
3. Learn key frontend concepts like **state lifting** and **state propagation**.
4. Begin contributing to the main project.

Each step will be marked by a **karate belt level** to signify your progress.

---

## 🥋 White Belt – Setting up the Project (5 min)

The **White Belt** represents the first step on your journey. This is where you learn the basic foundations of the project setup.

### Step 1: Initialize Vite and Storybook

1. **Create a new Vite project**:
   ```bash
   npm create vite@latest
   ```
2. **Install dependencies**:
   ```bash
   npm install
   ```
3. **Install and initialize Storybook**:
   ```bash
   npx sb init
   ```
4. **Start Storybook**:
   ```bash
   npm run storybook
   ```
   Once Storybook is running, you’ve earned your **White Belt**! 🥋

## 🥋 Yellow Belt – Creating a Basic Button Component (5 min)

The **Yellow Belt** signifies the mastery of the basics of component creation and documentation. You’ll create your first component and write a Storybook story to display it.

### Step 2: Create a Button Component

1.  **Create a `Button` component in `src/components/Button.jsx`**

    ```jsx
    import React from "react";

    const Button = ({ label, onClick }) => {
      return <button onClick={onClick}>{label}</button>;
    };

    export default Button;
    ```

2.  **Create a Storybook story for the `Button` component in `src/components/Button.stories.jsx`**:

    ```js
    import React from "react";
    import Button from "./Button";

    export default {
      title: "Example/Button",
      component: Button,
    };

    export const Primary = {
      args: {
        label: "Click Me",
      },
    };
    ```

Once you see your component in Storybook, congratulations! You’ve earned the **Yellow Belt**! 🥋

## 🥋 Orange Belt – Adding Advanced Props to the Button Component (5 min)

The **Orange Belt** introduces you to working with advanced props, controlling component behavior, and styling through CSS.

### Step 3: Enhance the Button Component

1. **Extend the `Button` component to support additional props: `backgroundColor`, `size`, and `primary`**:

```jsx
import React from "react";
import "./Button.css";

const Button = ({ label, onClick, backgroundColor, size, primary }) => {
  const mode = primary ? "button--primary" : "button--secondary";
  const sizeClass = `button--${size}`;

  return (
    <button
      onClick={onClick}
      className={`button ${mode} ${sizeClass}`}
      style={{ backgroundColor }}
    >
      {label}
    </button>
  );
};

export default Button;
```

2. **Write a CSS file `Button.css`**:

```CSS
.button {
  font-size: 16px;
  padding: 8px 16px;
  border: none;
  cursor: pointer;
}

.button--small {
  font-size: 12px;
}

.button--medium {
  font-size: 16px;
}

.button--large {
  font-size: 20px;
}

.button--primary {
  color: white;
}

.button--secondary {
  color: black;
}
```

3. **Update the Storybook story to provide controls for each prop**:

```js
import React from "react";
import Button from "./Button";

export default {
  title: "Example/Button",
  component: Button,
  argTypes: {
    backgroundColor: { control: "color" },
    size: {
      control: {
        type: "select",
        options: ["small", "medium", "large"],
      },
    },
    primary: { control: "boolean" },
  },
};

export const Primary = {
  args: {
    label: "Click Me",
    backgroundColor: "#ff0",
    size: "medium",
    primary: true,
  },
};
```

With this, you’ve learned to enhance components with dynamic props and CSS. Welcome to the **Orange Belt**! 🥋

## 🥋 Green Belt – Working with PropTypes and Default Values (5 min)

The **Green Belt** focuses on type-checking with `PropTypes` and setting default values for props.

### Step 4: Adding PropTypes and Default Values

1. **Update the `Button` component to include `PropTypes` and default values**:

```jsx
import React from "react";
import PropTypes from "prop-types";
import "./Button.css";

const Button = ({ label, onClick, backgroundColor, size, primary }) => {
  const mode = primary ? "button--primary" : "button--secondary";
  const sizeClass = `button--${size}`;

  return (
    <button
      onClick={onClick}
      className={`button ${mode} ${sizeClass}`}
      style={{ backgroundColor }}
    >
      {label}
    </button>
  );
};

Button.propTypes = {
  label: PropTypes.string.isRequired,
  onClick: PropTypes.func,
  backgroundColor: PropTypes.string,
  size: PropTypes.oneOf(["small", "medium", "large"]),
  primary: PropTypes.bool,
};

Button.defaultProps = {
  backgroundColor: "#007bff",
  size: "medium",
  primary: false,
};

export default Button;
```

2. **Test your changes in Storybook and ensure that default values are properly handled.**

You’ve now added PropTypes and default props to ensure robust components. You’ve earned the **Green Belt**! 🥋

## 🥋 Blue Belt – State Lifting in a Simple Sign-in Component (5 min)

State lifting is key for components that need to share data between parent and child components. In the **Blue Belt**, we’ll build a basic **Sign-in** form where state is lifted.

### Step 5: Lifting State in a Sign-in Form

1. **Create a `SignInForm` component that handles user input state**:

```jsx
import React, { useState } from "react";

const SignInForm = ({ onSubmit }) => {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();
    onSubmit({ email, password });
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label>Email:</label>
        <input
          type="email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
        />
      </div>
      <div>
        <label>Password:</label>
        <input
          type="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
        />
      </div>
      <button type="submit">Sign In</button>
    </form>
  );
};

export default SignInForm;
```

2. **Create a `SignInContainer` component to lift the state and handle the form submission**:

```jsx
import React from "react";
import SignInForm from "./SignInForm";

const SignInContainer = () => {
  const handleSignIn = (credentials) => {
    console.log("User signed in with", credentials);
  };

  return <SignInForm onSubmit={handleSignIn} />;
};

export default SignInContainer;
```

3. **Create a Storybook story for the `SignInContainer`**:

```js
import React from "react";
import SignInContainer from "./SignInContainer";

export default {
  title: "Example/SignInContainer",
  component: SignInContainer,
};

export const Default = {};
```

You’ve successfully lifted state within the sign-in form! **Blue Belt** unlocked! 🥋

## 🥋 Red Belt – State Propagation in a Sign-in Component (5 min)

Now, the **Red Belt** takes state propagation further by displaying the form input results in a separate component.

## Step 6: Propagating State in Sign-in

1. **Create a `SignInDisplay` component to show the submitted data**:

```jsx
const SignInDisplay = ({ email, password }) => {
  return (
    <div>
      <h3>Submitted Data:</h3>
      <p>Email: {email}</p>
      <p>Password: {password}</p>
    </div>
  );
};

export default SignInDisplay;
```

2. **Update `SignInContainer` to propagate state to the `SignInDisplay`**:

```jsx
import React, { useState } from "react";
import SignInForm from "./SignInForm";
import SignInDisplay from "./SignInDisplay";

const SignInContainer = () => {
  const [credentials, setCredentials] = useState(null);

  const handleSignIn = (data) => {
    setCredentials(data);
  };

  return (
    <div>
      <SignInForm onSubmit={handleSignIn} />
      {credentials && <SignInDisplay {...credentials} />}
    </div>
  );
};

export default SignInContainer;
```

You’ve mastered state propagation in the Sign-in component. Congratulations on earning your **Red Belt**! 🥋

## 🥋 Black Belt – Ready for Real Project Work

At the **Black Belt** level, you’ve mastered:

- Basic and advanced component creation.
- State management techniques like lifting and propagation.
- Writing robust components with PropTypes and default values.
- Managing and documenting your components with Storybook.

Now you’re ready to contribute to the main project! Keep the following in mind:

1.  Work on feature branches.
2.  Follow code review and pull request processes.
3.  Refer back to this guide or internal documentation when needed.

---

## 💡 Additional Resources

- [Vite Documentation](https://vite.dev/)
- [Storybook Documentation](https://storybook.js.org/docs)
- [React Documentation](https://react.dev/)

---

Good luck, and welcome to the team! We look forward to seeing your contributions. 🥋👊
