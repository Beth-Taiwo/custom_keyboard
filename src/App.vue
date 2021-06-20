<template>
  <keyboard />
</template>

<script>
import keyboard from "./components/customKeyboard.vue";
export default {
  name: "App",
  components: {
    keyboard,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
