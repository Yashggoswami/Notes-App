<template>
  <div class="main-container">
    <nav-bar class="nav-bar" @add-note="addNote($event)" />
    <dashboard-container
      class="dashboard"
      :add-note="addANote"
      @discard-note="addNote($event)"
    />
  </div>
</template>
<script>
import DashboardContainer from "@/components/Dashboard.vue";
import NavBar from "@/components/NavBar.vue";
export default {
  name: "DashboardView",
  components: { DashboardContainer, NavBar },
  data() {
    return {
      addANote: false,
    };
  },
  methods: {
    addNote: function (add) {
      this.addANote = add;
    },
  },
};
</script>
<style lang="scss">
.main-container {
  display: grid;
  grid-template-rows: auto 1fr;
  height: 100vh;
}
.nav-bar {
  grid-row: 1;
}
.dashboard {
  grid-row: 2;
}
</style>
