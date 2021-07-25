# Vue Events

<!-- ![](https://vuejsdevelopers.com/images/posts/generic_vue_header.jpg) -->

## Getting Started

- Fork and Clone
- `npm install`
- `npm run serve`

## Overview

In this lesson, we'll go in depth with handling and creating events in Vue. We saw a little bit of this in a previous lesson, but we'll go deeper into what events are and how they communicate within our application.

## What Are Events

Events are actions that are triggered during a certain behaviour being performed such as a `click` or `input`. Typically we can define these as user events. For example, when a user types into a form, this would trigger an `input` event. Or when a button is clicked, this would trigger a `click` event.

Events allow our application to be interactve which leads to a better user experience.

## Native Events

Like most web frameworks, Vue supports the standard browser event library. These include everything from `change` events to `keypress` events. These events are used in the same way that most others are, by declaring the event type on the element and the method to handle it. For example in React:

```jsx
<input onChange={someChangeFunction} />
```

Vue shares a very similar syntax which we've seen in a previous lesson with a `click` event:

```jsx
<button @click="doSomething">Press Me</button>
```

The big differentiator here is that Vue uses the `@` symbol to bind an event and the lack of `{}` to pass the function, string quotes are used instead.

Another way you can declare an event is by using the `v-on` directive and adding the event you want to watch for:

```jsx
<button v-on:click="doSomething">Press Me</button>
```

Both of these examples will give us the same output or behavior.

### Practicing With Events

In `App.vue`, you'll find the following jsx:

```jsx
<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <div class="form-container">
      <form>
        <input placeholder="Email" :value="email" name="email" type="email" />
        <input
          placeholder="Password"
          :value="password"
          name="password"
          type="password"
        />
        <button>Log In</button>
      </form>
    </div>
  </div>
</template>
```

You'll also find the following methods in the `script`:

```js
import './styles/app.css'
export default {
  name: 'App',
  components: {},
  data: () => ({
    email: '',
    password: ''
  }),
  methods: {
    handleFormChange() {},
    handleSubmit() {}
  }
}
```

Let's see how events operate in Vue.

Just like any event handler for forms, we'll want to accept the `event` object as an argument. Modify the `handleFormChange` method to accept an `event` parameter:

```js
handleFormChange(e) {},
```

Next we'll set the value of a piece of state using the event target name and event target value.

```js
handleFormChange(e) {
    this[e.target.name] = e.target.value
},
```

**We use bracket notation here to dynamically update a piece of state so we don't have to write more than one method, this only works because of the `name` attribute passed to the `input` elements. The `name` attributes value must match a key in our state**.

If you only had one piece of state to update you could use regular `dot` notation:

```js
handleFormChange(e) {
   this.someKey = e.target.value
},
```

Now that our `handleFormChange` is set up, we'll link it to the `input` elements. For the first `input` for the `email`, we'll use the `v-on` directive:

```jsx
  <div class="form-container">
      <form>
        <input placeholder="Email" :value="email" name="email" type="email" v-on:input="handleFormChange"/>
        <input
          placeholder="Password"
          :value="password"
          name="password"
          type="password"
        />
        <button>Log In</button>
      </form>
    </div>
```

For the second `input` element we'll use the `@` symbol:

```jsx
  <div class="form-container">
      <form>
        <input placeholder="Email" :value="email" name="email" type="email" v-on:input="handleFormChange"/>
        <input
          placeholder="Password"
          :value="password"
          name="password"
          type="password"
          @input="handleFormChange"
        />
        <button>Log In</button>
      </form>
    </div>
```

**The `v-on` and `@` symbol in this scenario are the same thing. The `@` is just short hand, just like using `:` is shorthand for `v-bind`.**
