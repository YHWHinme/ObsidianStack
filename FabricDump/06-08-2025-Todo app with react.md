# Building a To-Do List App with React

This video demonstrates building a to-do list application using React.js, covering the creation of components, state management, event handling, and styling with CSS.

## Setting up the Project [00:00:06]

*   A new JSX file, `todolist.jsx`, is created within the `src` folder.
*   This file contains a functional component named `ToDoList`.
*   The component is exported using `export default ToDoList`.

## Importing and Using React Hooks [00:00:27]

*   The `useState` hook is imported from `react` to manage state variables.
*   Two state variables are declared: `tasks` (an array of strings for to-do items) and `newTask` (a string for the currently typed task).
*   Their corresponding setter functions (`setTasks` and `setNewTask`) are also created.

## Defining Helper Functions [00:01:00]

*   Several functions are defined to handle user interactions:
    *   `handleInputChange`: Updates the `newTask` state based on input changes.
    *   `addTask`: Adds a new task to the `tasks` array.
    *   `deleteTask`: Removes a task from the `tasks` array.
    *   `moveTaskUp`: Moves a task up in the list.
    *   `moveTaskDown`: Moves a task down in the list.

## Building the UI [00:01:30]

*   A `div` with the class `todo-list` is created to hold the application's content.
*   An `h1` element displays "To-Do List".
*   An input element with a placeholder "Enter a task..." is used for task input.
*   A button labeled "Add" triggers the `addTask` function.
*   An ordered list (`ol`) is used to display the tasks.  The `map` method iterates through the `tasks` array.
*   Each task is rendered as a list item (`li`) with:
    *   A span element for the task text.
    *   Buttons for deleting, moving up, and moving down each task.

## Styling with CSS [00:03:46]

*   CSS is applied to style the application's elements.  Specific styles are applied to:
    *   The main container (`todo-list`).
    *   The `h1` element.
    *   Buttons (`.add-button`, `.delete-button`, `.move-button`).
    *   The input element.
    *   The ordered list (`ol`) and list items (`li`).
    *   The span element holding task text (`.text`).

## Implementing Functionality [00:08:50]

*   The `addTask` function is implemented to add new tasks.  Input validation ensures that empty tasks are not added.
*   The `deleteTask` function uses the `filter` method to remove a task based on its index.
*   The `moveTaskUp` and `moveTaskDown` functions use array destructuring to swap elements and update the task order.

## Conclusion [00:12:30]

The video concludes by demonstrating the fully functional to-do list application, showing the addition, deletion, and reordering of tasks.  The application starts with an empty task list.
