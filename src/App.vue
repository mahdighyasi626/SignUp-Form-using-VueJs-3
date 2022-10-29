<template>
<h1>akjsdlfjsld</h1>
  <SignupForm />
</template>

<script>
import SignupForm from './components/signupForm.vue'

export default {
  name: 'App',
  components: { SignupForm },
  data() {
    return {
      
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  margin: 0;
  padding: 0;
  background: #2c3e50;
}
</style>
