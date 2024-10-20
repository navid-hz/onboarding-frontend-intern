# 🥋 Frontend Onboarding Guide 🥋

#### Front-end Team Onboarding Guide for internship in WACOCO HQ

Welcome to the WACOCO **Front-end Team**! This guide will help you get started by walking you through the basics of setting up your environment and working on components, all while using the karate belt system to represent your progress. Each step should take about 5 minutes, and by the end of this guide, you'll be ready to dive into the real project.

## 🎯 Goal:

1. Set up a frontend project with **Vite** and **Storybook**.
2. Create and document components in **Storybook**.
3. Learn key frontend concepts like **state lifting** and **state propagation**.
4. Begin contributing to the main project.

Each step will be marked by a karate belt level to signify your progress.

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

---

## 🥋 Yellow Belt – Creating a Component and Writing a Story (5 min)

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

---

## 🥋 Green Belt – State Lifting (5 min)

The Green Belt represents an understanding of state management within components. In this step, you’ll learn how to lift state up to a parent component.

### Step 3: State Lifting

1. Create a `ButtonContainer` component to manage the button’s state in `src/components/ButtonContainer.jsx`:

```jsx
import React, { useState } from "react";
import Button from "./Button";

const ButtonContainer = () => {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Button clicked {count} times</p>
      <Button label="Click me" onClick={handleClick} />
    </div>
  );
};

export default ButtonContainer;
```

2. Add a Storybook story for `ButtonContainer` in `src/components/ButtonContainer.stories.jsx`:

```jsx
import React from "react";
import ButtonContainer from "./ButtonContainer";

export default {
  title: "Example/ButtonContainer",
  component: ButtonContainer,
};

export const Default = {};
```

You’ve successfully lifted state! **Green Belt** unlocked! 🥋

---

## 🥋 Blue Belt – State Propagation (5 min)

Achieving the Blue Belt means you’ve gained the ability to propagate state between components. In this step, we’ll create a child component that displays the lifted state.

## Step 4: State Propagation

1. Create a `Display` component to show the count in `src/components/Display.jsx`:

```jsx
import React from "react";

const Display = ({ count }) => {
  return <p>Button clicked {count} times</p>;
};

export default Display;
```

2. Modify `ButtonContainer` to pass the count state to the `Display` component:

```jsx
import React, { useState } from "react";
import Button from "./Button";
import Display from "./Display";

const ButtonContainer = () => {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <Display count={count} />
      <Button label="Click me" onClick={handleClick} />
    </div>
  );
};

export default ButtonContainer;
```

State is now properly propagated to the child component! **Blue Belt** achieved! 🥋

---

## 🥋 Black Belt – Ready for Real Project Work

By earning the Black Belt, you’ve mastered the basics of component development, state management, and Storybook integration. You’re now ready to contribute to the real project.

### Step 5: Start Contributing

At this point, you should:

- Be familiar with setting up the environment.
- Know how to create and document components.
- Understand basic state management patterns (lifting and propagation).

Now, it's time to check out the project repository and begin working on real tasks! Keep the following in mind:

1. Work on your own feature branches.
2. Follow the code review process by opening pull requests (PRs).
3. Use this guide or internal documentation for any questions or to refresh your knowledge.

---

## 💡 Additional Resources

---

Good luck, and welcome to the team! We look forward to seeing your contributions. 🥋👊
