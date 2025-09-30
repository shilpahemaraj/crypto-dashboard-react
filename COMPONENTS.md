# Crypto Dashboard React Project Documentation

## Overview
This project is a React-based cryptocurrency dashboard. It visualizes crypto data using reusable components and modern React practices.

## React Components Used

### 1. `App`
- **Definition**: The root component that manages the overall layout and routing of the dashboard.
- **Usage**: Renders the main sections and orchestrates the display of other components.

### 2. `Header`
- **Definition**: Displays the dashboard title, navigation, or branding elements.
- **Usage**: Placed at the top of the dashboard for consistent branding and navigation.

### 3. `CardSection`
- **Definition**: Shows summary cards for key crypto metrics (e.g., price, market cap).
- **Usage**: Used to present quick stats in a visually appealing card format.

### 4. `ChartSection`
- **Definition**: Renders charts for visualizing crypto trends and historical data.
- **Usage**: Integrates chart libraries to display price movements and other analytics.

## How Components Are Used
- The `App` component imports and renders `Header`, `CardSection`, and `ChartSection` to build the dashboard UI.
- Each section is modular, allowing for easy updates and maintenance.
- Data flows from parent (`App`) to child components via props, following React's unidirectional data flow.

## Example Usage
```jsx
import Header from './components/Header';
import CardSection from './components/CardSection';
import ChartSection from './components/ChartSection';

function App() {
  return (
    <div>
      <Header />
      <CardSection />
      <ChartSection />
    </div>
  );
}
```

## Component Concepts Explained
- **Component**: A reusable piece of UI in React, defined as a function or class.
- **Props**: Data passed from parent to child components to customize behavior or display.
- **State**: Internal data managed by a component, often used for interactivity.
- **Unidirectional Data Flow**: Data moves from parent to child, making the app predictable and easier to debug.

## Extending the Dashboard
- Add new components for additional features (e.g., news, portfolio tracking).
- Use props and state to manage dynamic data.
- Style components using CSS modules or styled-components for maintainability.

## Routing in the Dashboard
- **Current Status**: This project does not use React Router or any explicit routing mechanism. All components are rendered within the main `App` component, so navigation is handled by updating state and re-rendering components, not by changing routes.
- **How to Add Routing**: To support multiple pages (e.g., dashboard, settings), you can use the `react-router-dom` library. This involves wrapping your app in a `BrowserRouter` and using `Route` components to map URLs to React components.

## Lifecycle Methods: `componentDidMount`, `componentWillUnmount`, and `componentWillMount`

### `componentDidMount`
- **Definition**: A React lifecycle method called once after a component is mounted (inserted into the DOM).
- **Usage in Project**:
  - In `App`: Used to fetch initial crypto data and start a timer to refresh data every 2 seconds.
  - In `ChartSection`: Used to fetch chart data and start a timer for periodic updates.
- **Example**:
  ```js
  componentDidMount() {
    this.fetchData();
    this.interval = setInterval(() => this.fetchData(), 2000);
  }
  ```

### `componentWillUnmount`
- **Definition**: Called just before a component is removed from the DOM. Used for cleanup (e.g., clearing timers).
- **Usage in Project**:
  - In `App` and `ChartSection`: Clears the interval timer to prevent memory leaks.
- **Example**:
  ```js
  componentWillUnmount() {
    clearInterval(this.interval);
  }
  ```

### `componentWillMount`
- **Definition**: Was called before a component was mounted. Deprecated in recent React versions and not used in this project.
- **Best Practice**: Use `componentDidMount` for data fetching and setup instead.

---
For more details, refer to the source code in the `src/components` directory.
