<template>
  <div>
    <HelloWorld />
    <router-view />
  </div>
</template>

<script>
import HelloWorld from "@/components/NavBar.vue";

export default {
  components: {
    HelloWorld,
  },
};
</script>

<style></style>
