<template>
  <header class="header">
    <nav class="navbar">
      <div class="left">
        <h1 class="heading-app">My Notes App</h1>
      </div>
      <div class="right">
        <ul class="nav-list">
          <li class="nav-list-item" @click="$emit('add-note', true)">
            Add Note
          </li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: "NavBar",
};
</script>

<style>
.header {
  top: 0;
  position: sticky;
  z-index: 19999;
}
.navbar {
  width: 100%;
  height: 100%;
  max-height: 100px;
  display: grid;
  grid-template-areas: "left right right right";
  grid-template-columns: 1fr 3fr;
  grid-template-rows: 100%;
  background-color: black;
  color: white;
  position: sticky;
}
.heading-app {
  padding-left: 2rem;
}
ul {
  margin: 0;
  height: 100%;
  display: flex;
  flex-direction: row-reverse;
  padding-right: 2rem;
  text-decoration: none;
  list-style-type: none;
}
li {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
}
.nav-list-item {
  background-color: aliceblue;
  color: black;
  cursor: pointer;
  margin: 1rem 0;
  padding: 0 1rem;
  border-radius: 10px;
}
.nav-list-item:hover {
  text-decoration: solid;
}
</style>
