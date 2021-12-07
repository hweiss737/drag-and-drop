<template>
<div class="component-body">
  <drag-drop 
    header="Drag 'n Drop" 
    :original-items="originalItems"
    :show-handle="handleProp" 
    :show-delete="deleteProp"
    :show-enumeration="enumerationProp"
    :show-add="addProp" />
  <div class="header props-header">Properties</div>
    <div class="block">
        <div class="props-row">
            <label class="property">Handle</label>
            <toggle v-on:toggleSlider="toggleHandleSlider($event)" />
        </div>
        <div class="props-row">
            <label class="property">Delete</label>
            <toggle v-on:toggleSlider="toggleDeleteSlider($event)" />
        </div>
        <div class="props-row">
            <label class="property">Enumeration</label>
            <toggle v-on:toggleSlider="toggleEnumerationSlider($event)" />
        </div>
        <div class="props-row">
            <label class="property">Add</label>
            <toggle v-on:toggleSlider="toggleAddSlider($event)" />
        </div>
    </div>
  </div>
</template>

<script>
import DragDrop from './DragDrop.vue'
import Toggle from './Toggle.vue'
export default {
  components: {
      DragDrop,
      Toggle
  },
  data () {
    return {
      handleProp: false,
      deleteProp: false,
      enumerationProp: false,
      addProp: false,
      originalItems: [
        'Item 1',
        'Item 2',
        'Item 3'
      ]
    }
  },
  methods: {
    toggleHandleSlider(event) {
      this.handleProp = event;
    },
    toggleDeleteSlider(event) {
      this.deleteProp = event;
    },
    toggleEnumerationSlider(event) {
      this.enumerationProp = event;
    },
    toggleAddSlider(event) {
      this.addProp = event;
    }
  }
};
</script>

<style>
@import '../assets/main.css';
.property {
  font-family: "Lato", Helvetica, Arial;
  color: #343434;
  width: 90%;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}
</style>