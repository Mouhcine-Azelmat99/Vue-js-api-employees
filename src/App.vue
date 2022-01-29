<template>
  <div id="app" class="container">
    <Employees />
  </div>
</template>
<script>
import  Employees from './components/Employees.vue';

export default ({
  name : "App",
  components : {
    Employees
  }
})
</script>
