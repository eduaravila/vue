<template>
  <button @click="function_click">hola dame click bb {{nombre_bb}}</button>
</template>

<script>
export default {
  name: "custom_button",

  props: {
    function_click: Function,
    nombre_bb: String,
    color: String
  }
};
</script>

<style>
button {
  color: red;
  background: black;
}
</style>