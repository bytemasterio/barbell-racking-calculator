# Install vue cli
npm install -g vue-cli

# Create project
npm init webpack platecalc

# Vue cli Setup
? Project name platecalc
? Project description A Vue.js project
? Author Matt Froese <froese.matt@gmail.com>
? Vue build standalone
? Install vue-router? No
? Use ESLint to lint your code? No
? Set up unit tests No
? Setup e2e tests with Nightwatch? No
? Should we run `npm install` for you after the project has been created? (recommended) npm

# To get started:

cd platecalc
npm run dev

# Browser

open your browser to ``http://localhost:8080``

# App.vue

The cli comes preloaded with an App.vue and a demo component called HelloWord. For the sake of this app, we will only need our main component. Go ahead and remove components/HelloWorld.vue and remove the reference in App.vue

Your App.vue should look something like the following

```
<template>
  <div id="app">
    <h1>Plate Calc</h1>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```

Now we need a variable to hold our weight base value for the plate calculator and an array for the plates needed for that weight. Add a data function with a weight value and default it to 45

```
export default {
  name: 'App',
  data() {
      return {
          weight: 50,
					plates: []
      }
  }
}
```

Now we can add an input to change this value.

```
<input type="number" v-model="weight" step="5" min="45" /> lbs
```

## Calculating plates

To calculate the plates needed we first need a method that runs every time the weight is changed. Create a calculate method in your vue component.

```
methods: {
		calculate() {

		}
}
```
