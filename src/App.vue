<template>
  <SignupForm />
</template>

<script>
  import SignupForm from '@/components/SignupForm.vue'
  export default {
    name: 'App',
    components: {
      SignupForm
    }
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin: 60px auto;
  }

  body {
    margin: 0;
    background: rgb(208, 208, 208);
    box-sizing: border-box;
    margin: 0 auto;
    text-align: center;
  }
</style>
