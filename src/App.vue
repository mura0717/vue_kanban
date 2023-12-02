<template>
  <div id="app">
    <div style="columns: 3">
      <iframe
        src="https://giphy.com/embed/gEosD4s6fhCUuyfrPC"
        width="120"
        height="120"
        frameBorder="0"
        class="giphy-embed"
        allowFullScreen
      ></iframe>
      <p>
        <a
          href="https://giphy.com/gifs/misslizznl-kanban-ruijter-to-do-sticky-gEosD4s6fhCUuyfrPC"
        ></a>
      </p>
      <iframe
        src="https://giphy.com/embed/aH6pGXuL7LdzLi5C9j"
        width="120"
        height="120"
        frameBorder="0"
        class="giphy-embed"
        allowFullScreen
      ></iframe>
      <p>
        <a
          href="https://giphy.com/gifs/misslizznl-agile-kanban-ruijter-aH6pGXuL7LdzLi5C9j"
        ></a>
      </p>
      <iframe
        src="https://giphy.com/embed/DaEjBX6gkJyR9nFtL7"
        width="120"
        height="120"
        frameBorder="0"
        class="giphy-embed"
        allowFullScreen
      ></iframe>
      <p>
        <a
          href="https://giphy.com/gifs/misslizznl-agile-kanban-yellow-sticky-DaEjBX6gkJyR9nFtL7"
        ></a>
      </p>
    </div>

    <KanbanBoard msg="Welcome to Easy Kanban" />
  </div>
</template>

<script>
import KanbanBoard from "./components/KanbanBoard.vue";

export default {
  name: "App",
  components: {
    KanbanBoard,
  },
};
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
