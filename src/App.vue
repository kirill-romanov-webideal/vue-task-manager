<template>
  <div id="app">
    <dashboard :tasks.sync="tasks" />
  </div>
</template>

<script>
import Dashboard from "./components/Dashboard";

export default {
  name: 'app',
  components: {
    Dashboard
  },
  data() {
    return {
      tasks: [
        {
          id: 1,
          assigned: '',
          status: 'opened',
          title: 'opened',
          description: ''
        },
        {
          id: 2,
          assigned: '',
          status: 'working',
          title: 'working',
          description: ''
        },
        {
          id: 3,
          assigned: '',
          status: 'closed',
          title: 'Closed',
          description: 'Closed'
        },
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding: 30px;
}
</style>
