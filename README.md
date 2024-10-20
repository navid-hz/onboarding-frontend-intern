# 🥋 Frontend Onboarding Guide 🥋

## Front-end Team Onboarding Guide for internship in WACOCO HQ

Welcome to the WACOCO **Frontend Team**! This guide will help you get started by walking you through the basics of setting up your environment and working on components, all while using the karate belt system to represent your progress. Each step should take about 5 minutes, and by the end of this guide, you'll be ready to dive into the real project.

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
   `bash
 npm run storybook
 `
   Once Storybook is running, you’ve earned your White Belt! 🥋

---

## 🥋 Yellow Belt – Creating a Component and Writing a Story (5 min)

The **Yellow Belt** signifies the mastery of the basics of component creation and documentation. You’ll create your first component and write a Storybook story to display it.

### Step 2: Create a Button Component

1.  **Create a Button component in src/components/Button.jsx**

    ```jsx
    import React from "react";

    const Button = ({ label, onClick }) => {
      return <button onClick={onClick}>{label}</button>;
    };

    export default Button;
    ```

2.  **Create a Storybook story for the Button component in src/components/Button.stories.jsx**:

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

    Once you see your component in Storybook, congratulations! You’ve earned the Yellow Belt! 🥋
