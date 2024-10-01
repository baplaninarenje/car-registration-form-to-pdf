<template>
  <div id="app">
    <CarRegistrationForm />
  </div>
</template>

<script>
import CarRegistrationForm from './components/CarRegistrationForm.vue';

export default {
  components: {
    CarRegistrationForm
  }
};
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
</style>
