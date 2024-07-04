<template>
  <div>
    <SignUp />
  </div>
</template>

<script>
import SignUp from "./components/SignUp";

export default {
  name: "App",
  components: {
    SignUp,
  },
};
</script>

<style>
#app {
  font-family: Avenir, sans-serif;

  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
