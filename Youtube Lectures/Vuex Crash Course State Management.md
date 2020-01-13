---
Date: 2020/1/6
Length: 1:01:18
Video: Vuex Crash Course | State Management
Channel: Traversy Media
Source: https://www.youtube.com/watch?v=5lVQgZzLMHc
---

## Intro (00:00)

What is Vuex?

- State management & pattern library
- centralized store for all components

Why use it?

- Components need to share state in many cases
- No need to pass events up/down through multiple components
- Global state is "reactive"

---

## Vuex Terms (3:25)

<u>**State**</u>: App-level state/data.  
<u>**Getters**</u>: Get pieces of state values.  
<u>**Actions**</u>: Called from components to commit a mutation.  
<u>**Mutations**</u>: Updates the state.  
<u>**Modules**</u>: Each module can have it's own state, getters, actions & mutations.

---

## Start of code! (4:35)

(Shows the finished app, recommends downloading dev tools for Chrome)  
(Install vue cli globally)  
(Use `vue create` to create the app boilerplate)  
(Install axios & vuex)

---

## Create Todos component (8:15)
