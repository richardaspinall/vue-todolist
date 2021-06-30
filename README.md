# Vue.js TodoList

> **Date started**: 25 April 2021

> **Date ended**: 3 May 2021

## Description

TodoList learning project for Vue.js.

---

## Requirements

- NPM ~7.6.3

## Install

- `npm install`

## Development

- `npm run serve`

- `npm run build` then `serve -s dist` (using serve - NPM package)

---

# Project outline

## Goals

- [x] Learn the basics of Vue.js
- [x] Create a TodoList application
- [x] Stay within the requirements and don't go down rabbit holes
- [x] ~~Complete within 4 hours~~ > I ended up going a little over (30 min) but as I knew my time was up, it was super focussed tidy up items.

## App requirements

- [x] Single page of todo items
- [x] Able to add remove and edit todos
- [x] Saves to browser storage
- [ ] ~~Use CSS framework~~ I ended up not doing any work with CSS and just focussed on Vue

## Results

Although it's not pretty, behind the scenes a lot of foundational learning went on. I ran out of time to actually do any styling and I wanted to be strict on myself about time and rabbit holes.

I started to see the power of using a framework like Vue (I've had minimal exposure to these frameworks and libraries such as React, Angular, etc). I can already see that I could refactor what I ended up with, or add a centralized store (lightly read up on)

I spent a tad too long debugging Travis CI. This caused me to stretch out an extra hour but I stopped as soon as I got it working. I will look to learn about CI in a separate project.

<img width="500" alt="example" src="https://github.com/richardaspinall/vuejs-todolist/blob/main/docs/TodoList.png">

### What I learned

#### Hard Skills

- Basics of Vue.js: how the framework and structure works.
- How to use the Vue CLI and create an app through it
- V directives and life cycle methods.
- How data via props flows down through components

#### Soft Skills

- Focussed on official documentation gets me very far! I only watched a very short video on using the CLI and a couple of small clips. No tutorial watching / following along.
- Time boxing a project at a high level and then breaking it down to small sprints was super effective. As soon as I was at my 4 hour deadline, it made me super focussed on fixing anything that didn't meet my goals so I ended up only going slightly over.

### The coding experience steps

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

- 4 hours is up!

- Going slightly over: everything seemed to be working well until I tried on mobile – the "add" button wasn't working when I tapped on it. I did some searching and got pointed in the wrong direction: `v-on:click` was only for mouses, and I needed to use another `tap` or `press` etc method. Nothing seemed to work though. I eventually realized I had manually initialized the array in the local storage on my computer when I was testing and hadn't automated that when you open the app for the first time!

- Decided to get Travis CI to build the app to Github Pages. Had a bit of trouble following some instructions and specifically setting enviornment variables from the command line as per the following guide. As soon as I set within the Travis web UI, everything worked fine. https://cli.vuejs.org/guide/deployment.html#platform-guides

## Resources

- [Create, Build, and Serve Apps with the Vue CLI](https://www.youtube.com/watch?app=desktop&v=WmrawkHYMTg&feature=youtu.be)
- [Vue.js CLI](https://cli.vuejs.org/guide/creating-a-project.html#vue-create)
- [Vue.js Documentation](https://cli.vuejs.org/guide/)
- [Building to Github Pages](https://cli.vuejs.org/guide/deployment.html#platform-guides)
- [Travis CI](https://docs.travis-ci.com/)
