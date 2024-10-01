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
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
}
</style>