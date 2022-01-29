<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <Employees msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import Employees from "@/components/Employees.vue";

export default {
  name: "Home",
  components: {
    Employees,
  },
};
</script>
