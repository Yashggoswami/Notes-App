<template>
  <dashboard-view />
</template>
<script>
import DashboardView from "./views/DashboardView.vue";
export default {
  name: "App",
  components: { DashboardView },
};
</script>
<style lang="scss">
body {
  margin: 0;
  font-family: Arial, sans-serif;
}
</style>
