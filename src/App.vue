<template>
  <drag-drop-container header="Drag 'n Drop" />
</template>

<script>
import DragDropContainer from "./components/DragDropContainer.vue";

export default {
  components: {
    DragDropContainer
  },
};
</script>

<style>
html { 
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  background-color: #E3E2DF;
  height: 100%;
}
body {
  height: 100%;
}
#app {
  display: flex;
  justify-content: space-around;
  height: 100%;
}
</style>
