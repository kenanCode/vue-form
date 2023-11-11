<template>
  <h1> TechKnow Magazine Signup </h1>
  <p id="topLine"> Sign up to our magazine and receive info tailored to your interests and skills. </p>
<SignUp />
</template>

<script>
import SignUp from './components/SignUp.vue'

export default {
  name: 'App',
  components: { SignUp }
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
  background: #eee;
}

h1{
  color: black;
}

#topLine {
  color: black;
}
</style>
