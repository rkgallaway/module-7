# LAB: Context API - Behaviors

**To Do List Manager Phase 2:** Incorporate configuration settings to the application

In this phase, we'll be adding an editor so that users can save their preferences for the application, allowing them to change some of the default behaviors

## Before you begin

Refer to *Getting Started*  in the [lab submission instructions](https://codefellows.github.io/code-401-javascript-guide/reference/submission-instructions/labs/) for complete setup, configuration, deployment, and submission instructions.

1. Continue to work in your GitHub Repository named `todo-app`
1. Create and work in a new branch for today called 'context-methods'

## Business Requirements

Refer to the [To Do System Overview](../../apps-and-libraries/todo/README.md) for a complete review of the application, including Business and Technical requirements along with the development road map.

## Phase 2 Requirements

In Phase 2, we're going to extend the functionality of our application by allowing the user to make some decisions on how they would like the application to function. Specifically, we'll let them make changes to 2 settings.

- Implement the Context API to make some basic application settings available to components
  - How many To Do Items to show at once
  - Whether or not to show completed items
- Provide the users with a form where they can change the values for those settings
  - This should be given in the form of a new component, perhaps linked to from the main navigation
  - *Hint: Use Browser Router to create the page/route/component for this*
  - Once settings are updated, render the updated settings to the right of the "form".  Consider using `Grid`, `Card`, and `When` components.
- Save the user preferences in Local Storage
- Retrieve their preferences from Local Storage and apply them to the application on startup

#### ToDo Comp

![To Do with Pagination](todo.png)

#### Settings Comp

![Settings Page](settings.png)


## Technical Requirements / Notes

> Technical requirements for the core application are unchanged from the prior phases, with the addition of context behaviors defined in our global Context Provider

1. Extend your `context` provider to include all of the following features:
   - Create a `context` for managing application settings and provide this at the application level.
   - Display or Hide completed items (boolean).
   - Number of items to display per screen (number).
   - Default sort field (string).
   - Create a function in your context that saves user preferences (for the above) to local storage.
   - Implement a `useEffect()` (or `componentDidMount()`) in your context to read from local storage and set the values for those 2 state properties on application load.
   > Note: You will need to `stringify` your state prior to saving to local storage, and parse it when you retrieve it.

1. Consume and utilize `Context` values throughout your components:
    - Show a maximum of a certain number of items per screen in the `<List />` component.
      - Properly implement the Mantine `Pagination` component functionality to let the users navigate a long list of items with the correct number of tasks showing per "page".
    - Hide or show completed items in the list.

### Application Structure (proposed)

In this proposal:

- `styles.scss` files may or may not be necessary for each component
- unit tests are placed in the component directory (testing one file only)
- integration tests are placed in the `__tests__` directory (testing more than one file)

```text
├── public
├── src
│   ├── __tests__
│   │   │   └── empty for now...
│   ├── Components
│   │   ├── AddForm
│   │   │   └── AddForm.jsx
│   │   ├── Footer
│   │   │   └── Footer.jsx
│   │   ├── Header
│   │   │   └── Header.jsx
│   │   ├── List
│   │   │   └── List.jsx
│   │   ├── SettingsForm
│   │   │   └── SettingsForm.jsx
│   │   ├── Todo
│   │   │   └── ToDo.jsx
│   │   │   └── styles.scss  
│   ├── Context
│   │   ├── Settings
│   │   │   └── Settings.jsx
│   │   │   └── settings.test.js
│   ├── hooks
│   │   └── form.js
│   ├── App.js
│   ├── index.js
├── .gitignore
├── package-lock.json
├── package.json
└── README.md
```

### Stretch Goal:

- Sort the items based on any of the keys (i.e. difficulty).
- Update the state handling for todo items to use `useReducer()` vs separate state management methods

### Testing

- Tests should assert all behavioral functionality
- Do a deep mount of the app, and set tests to make assertions on the child components that consume context from the Provider.
  - Can they see context?

### Assignment Submission Instructions

Refer to the the [Submitting React Apps Lab Submission Instructions](https://codefellows.github.io/code-401-javascript-guide/reference/submission-instructions/labs/react-apps.html) for the complete lab submission process and expectations
