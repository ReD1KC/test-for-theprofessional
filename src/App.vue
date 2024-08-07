<template>
  <div id="app">
    <Vacancies />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Vacancies from "./components/Vacancies.vue";

export default defineComponent({
  name: "App",
  components: {
    Vacancies,
  },
});
</script>

<style>
/* Добавьте стили по необходимости */
</style>
