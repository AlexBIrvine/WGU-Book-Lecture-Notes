---
Date: 2020/1/4
Length: 1:08:52
Video: Vue JS Crash Course
Channel: Traversy Media
Source: https://www.youtube.com/watch?v=Wy9q22isx3U
---

## Intro (00:00)

<u>**What is Vue?**</u>: Progressive & performance JS framework for building UIs.

- Helps create UIs easier
- Less of a learning curve than react/angular
- fast & lightweight
- Virtual DOM
- SPA focused

<u>**The app we will build**</u>:

![App to build](./img/Vue1.jpg)

3 parts: Output, functionality & style.

We will get started using VUE-CLI 3.

- Includes Babel, typescript, eslint, postCSS, etc.,
- Dev server with hot reload
- VUE UI tool to manage app in a graphical interface

VUEX (covered in a different video), will handle state.

---

## Installing & setting up tools (7:15)

Install Vue.js dev tools extension, install NODE.js, VUE CLI.

Run `vue create <name>` to create a project with command line.  
Run `vue ui` to start the Vue UI dashboard.

---

## Overview of files created with vue CLI (13:30)

<u>**package.json**</u>

- lists dependencies & scripts (serve, build, lint)

<u>**public/index.html**</u>

- the page that is served in the browser.
- Vue creates SPA (single page applications), so this is the file that loads.

<u>**src/main.js**</u>

- The entry point to vue.
- Where vue & main app component is imported.
- Where vue is mounted to element with id app.

<u>**src/App.vue**</u>

- The main component for the application.
- This example imports the `<HelloWord>` component.

<u>**src/components**</u>

- The folder where the site components are stored.

(We then deleted most of the default code & insert normalizing styling into App.vue)

---

## Data (19:30)

Added data to `App.vue`'s script section found in the following code:

```javascript
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Todo One",
          completed: false
        },
        {
          id: 2,
          title: "Todo Two",
          completed: true
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false
        }
      ]
    };
  }
```

---

## Creating new component (21:43)

Created `src/components/Todos.vue` & added the following code:

1. Added template, script, style tags.
2. Added our div tag to template.  
   <u>**NOTE**</u>: Each component needs a single root element to work off of. div by convention.
3. Added `name: "Todos"` to the script tag.

Imported `Todos.vue` in `App.vue`

1. Used `import Todos from "./components/Todos";` in script tag.
2. Added `Todos` to components property in script tag.
3. Added Todos element to template.

---

## Passing todos from App.vue into Todos.vue (23:35)

We will pass the data with `v-bind` directive.  
This binds the data `todos` to the component.  
Modified the Todos tag to become this:

```js
<Todos v-bind:todos="todos" />
```

In `Todos.vue`, added `props: ["todos"]` to the script tag.

---

## Looping through an array (24:35)

We can loop through items with the `v-for` directive.  
When we loop in this manner, each element created by the loop needs to have a unique key.  
We assign this key with `v-bind:key` directive.

Here is the full code for looping through the todo data & outputting the titles:

```js
<div v-bind:key="todo.id" v-for="todo in todos">
  <h3>{{ todo.title }}</h3>
</div>
```

---

## Creating TodoItem.vue component (26:00)

Steps taken:

1. Created file in component directory.
2. Created template, script, style elements.
3. Added `name: "TodoItem"` to script.
4. Copy pasted style.
5. Imported TodoItem into Todos
   1. Added import statement to script element.
   2. Added `TodoItem` to components in script element.
   3. Added TodoItem element to template element.
6. Bound todo data to TodoItem element. Code in Todos template so far:

```js
<div v-bind:key="todo.id" v-for="todo in todos">
  <TodoItem v-bind:todo="todo" />
</div>
```

7. Added `props: ["todo"]` into `TodoItem.vue`'s script.
8. Updated TodoItem.vue template to show todo.title.

---

## Implement .is-complete (29:34)

We used `v-bind:class` on the TodoItem to set the class of the element to `.is-complete` if the completed property in the todo object is true.

Code so far for `TodoItem.vue`'s template element:

```js
<div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
  <p>{{ todo.title }}</p>
</div>
```

---

## Toggle complete with event (31:30)

Added a checkbox to the TodoItem.  
Used the `v-on:change` directive to bind the change of the checkbox with a method called `markComplete`.  
Added `methods:` to `TodoItem` script element, then added `markComplete()` to it.

```js
methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
```

---

## Deleting Todo items (34:30)

Add button to TodoItem template.

We'll need to "go up" in our component stack to access the todos array from our TodoItem.  
We will do this by emmitting an event. The event emit function can accept parameters, and we'll add the `todo.id` to that.  
Button code:

```html
<button @click="$emit('del-todo', todo.id)" class="del">x</button>
```

We then catch this event in `Todos.vue` & pass it up to `App.vue`.

```html
<div v-bind:key="todo.id" v-for="todo in todos">
  <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
</div>
```

Finally we catch it in `App.vue`, create a method to work on it, then use the filter array method to return a new list without the deleted item.

```html
<div id="app">
  <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
</div>
```

```js
methods: {
  deleteTodo(id) {
    this.todos = this.todos.filter(todo => todo.id !== id);
  }
}
```

---

## Adding header to page (39:50)

Steps taken:

1. Created a `Layout/` folder inside `Components/`
2. Created `Header.vue`, which is simple
3. Imported `Header.vue` into `App.vue`
4. Added Header to top of app.

---

## Adding ADD form (41:50)

Steps taken:

1. Created `AddTodo.vue` inside `Components/`
2. Added basic innards
3. Added `AddTodo` into `App.vue`
4. Added data() to `AddTodo`, only holds object with property `title`
5. Used the `v-model` directive to bind data to form.
6. Added `@submit="addTodo"` to the form element

Code inside `AddTodo.vue` template element:

```html
<div>
  <form @submit="addTodo">
    <input type="text" v-model="title" name="title" placeholder="Add Todo..." />
    <input type="submit" value="submit" class="btn" />
  </form>
</div>
```

7. Created `methods: {}` inside script element then added`addTodo()` to it
8. Installed `UUID` with terminal command `npm i uuid`, imported in `AddTodo.vue`, used it in `addTodo()`

Code inside addTodo():

```js
  methods: {
    addTodo() {
      e.preventDefault();

      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false
      };

      //Send up to parent
      this.$emit("add-todo", newTodo);

      this.title = "";
    }
  }
```

9. In `App.vue`, added `v-on:add-todo="addTodo"` to AddTodo element
10. Created `addTodo(newTodo)` method to `methods:`

Code inside addTodo(newTodo):

```js
AddTodo(newTodo) {
  this.todos = [...this.todos, newTodo];   // Uses spread operator to copy old value & add newTodo
}
```

---

## HTTP request to backend (50:40)

Using something called "JSONPlaceholder". Uses JSON file as a backend.

Steps taken:

1. Installed axios using `npm i axios`, then imported it in `App.vue`
2. After `methods:` in `App.vue` script element, made a function called `created()`. This will run right away since it's outside of `methods:`

(JSONplaceholder site has changed their api endpoints. This tutorial no longer works)

---

## Vue Router (1:00:00)
