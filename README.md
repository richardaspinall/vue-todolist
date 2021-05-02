# Vue.js TodoList

> **Date started**: (April 2021)

> **Date ended**:

## Description

Learning project for Vue.js

---

## Requirements

- Requirements for installation

## Install

- How to install

## Development

- `npm run serve`

## Production

Run `npm run build` then `serve -s dist` (using serve - NPM)

## Usage

- How to use

---

# Project outline

## Goals

- [ ] Learn the basics of Vue.js
- [ ] Create a TodoList application
- [ ] Stay within the requirements (don't go down rabbit holes)
- [ ] Complete within 4 hours

## V1 requirements

- [ ] Single page of todo items
- [ ] Able to add remove and edit todos
- [ ] Saves to browser storage
- [ ] Use CSS framework

## Results

### What I learned

### The coding experience

[Screenshot of the project working]

## Steps

### 1. Created readme with goals and outline of the project

### 2. Researched / follow tutorials

- High level look and set up of Vue via CLI [Create, Build, and Serve Apps with the Vue CLI](https://www.youtube.com/watch?app=desktop&v=WmrawkHYMTg&feature=youtu.be)

- Skimmed through documentation: https://v3.vuejs.org/guide/introduction.html & https://cli.vuejs.org/guide/

### 3. Scaffolded app

- Via the above tutorial and the following: https://cli.vuejs.org/guide/creating-a-project.html#vue-create

### 4. Read through documentation

- https://vuejs.org/v2/guide/

### 5. Learned about components and the module system

- https://vuejs.org/v2/guide/single-file-components.html
- https://vuejs.org/v2/guide/components-registration.html#Module-Systems

### 6. Tinkering with the app

- Navigating around the scaffolded app and testing out how things connect
- Removed the router as I won't need that for this app
- Learned about props vs data

### 7. Code: Built out TodoList and Todo components

- In the root of the application (App.vue), I added the mounted() lifecycle hook to get the TodoList array from the local storage of the browser. I then pass that down as a property to the TodoList component. Using the browser storage requires serialization of the array as a string and store that (as you can't store JSON)

- In the TodoList component (`components/TodoList.vue`), I created a template that that loops through the TodoList creating todos. I quickly realized each of the todos should be their own components so that we can bind a delete method to each of them. I instead then pass the specific todo and the array as properties down to a Todo component.

- In the Todo component I display the todo text and a button to delete this todo next to it.

- We now need need to be able to add and delete todos. I added an input and binded the value with `v-model` to the data property of the component so we can easily add this to the array either with the `enter` key press or clicking the add button. The add method then simply saves the updated TodoList to storage and I added a check to ensure we can't add empty strings or spaces. As soon as we push to the array, the component rerenders and we can see our added todo.. beautiful!

- Back in the Todo component I added a delete method to delete the todo. It simply finds the index of the todo and splices its self out, then saves the updated TodoList to storage.

- Everything seemed to be working well until I tried on mobile – the "add" button wasn't working when I tapped on it. I did some searching and got pointed in the wrong direction: `v-on:click` was only for mouses, and I needed to use another `tap` or `press` etc method. Nothing seemed to work though. I eventually realized I had manually initialized the array in the local storage on my computer when I was testing and hadn't automated that when you open the app for the first time!

- 4.5 hours is up!

## Resources

- [Create, Build, and Serve Apps with the Vue CLI](https://www.youtube.com/watch?app=desktop&v=WmrawkHYMTg&feature=youtu.be)
- [Vue.js CLI](https://cli.vuejs.org/guide/creating-a-project.html#vue-create)
- [Vue.js Documentation](https://cli.vuejs.org/guide/)
