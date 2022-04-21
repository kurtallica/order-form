<template>
  <img alt="Basket logo" src="./assets/logo.png" />
  <OrderForm msg="GREETINGS FROM THE ORDER FORM" />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import OrderForm from "./components/OrderForm.vue";

export default defineComponent({
  name: "App",
  components: {
    OrderForm,
  },
});
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
