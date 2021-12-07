<template>
  
    <label class="header">{{ header }}</label>
    <div v-if="items.length > 0" class="block">
      <draggable class="draggable-area" :handle="showHandle ? '.bars-icon' : '.item'" :list="items">
        <div 
          class="item-row"
          v-for="item, index in items" 
          :key="index">
            <div class="item">
              <label>{{itemLabel(item, index)}}</label>
              <div v-if="showHandle">
                <i class="fas fa-bars bars-icon"></i>
              </div>
            </div>
            <div v-if="showDelete" class="trash-icon" @click="deleteItem(item)">
              <i class="fas fa-trash"></i>
            </div>
        </div>
      </draggable>
    </div>
    <div v-if="showAdd" class="block add-container">
      <input 
        id="add-input" 
        class="add-input" 
        autocomplete="off" 
        placeholder="Add Item" 
        v-model="newItem" 
        v-on:keyup.enter="addItem(newItem)" />
      <div class="add-icon" @click="addItem(newItem)">
        <i class="fas fa-plus-square"></i>
      </div>
    </div>
</template>

<script>
import { VueDraggableNext } from 'vue-draggable-next'
export default {
  props: {
    header: String,
    showHandle: {
      type: Boolean,
      default: false
    },
    showDelete: {
      type: Boolean,
      default: false
    },
    showEnumeration: {
      type: Boolean,
      default: false
    },
    showAdd: {
      type: Boolean,
      default: false
    },
    originalItems: {
      type: Array,
      default: function(){
        return [];
      }   
    }
  },
  components: {
    draggable: VueDraggableNext,
  },
  data () {
    return {
      newItem: '',
      items: this.originalItems
    }
  },
  methods: {
    itemLabel(item, index){
      if(this.showEnumeration){
        return (index+1) + '. ' + item;
      }
      return item;
    },
    deleteItem(e){
      this.items = this.items.filter(item => item !== e);
    },
    addItem(e){
      if(e.trim() !== ''){
        this.items.push(e);
        this.newItem = '';
      }
    }
  }
};
</script>

<style scoped>
@import '../assets/main.css';

.draggable-area {
  display: flex;
  flex-direction: column;
}
.item-row {
  width: 100%;
  display: flex;
  margin-bottom: 5px;
  margin-top: 5px;
  justify-content: space-between;
  align-content: center;
}
.item {
  font-family: "Lato", Helvetica, Arial;
  color: #343434;
  width: 90%;
  border-radius: 3px;
  box-shadow: 0 1px 2px rgb(0 0 0 / 0.2);
  padding: 10px;
  display: flex;
  justify-content: space-between;
}
.bars-icon {
  color: lightgray;
  cursor: grab;
}
.trash-icon {
  color: #880808;
  cursor: pointer;
  align-self: center;
  margin-left: 12px;
}
.add-container {
  width: 80%;
  display: flex;
  padding: 20px;
  justify-content: space-between;
  align-content: center;
}
.add-input {
  border-radius: 3px;
  border-color: rgb(0 0 0 / 0.2);
  width: 80%;
  font-family: "Lato", Helvetica, Arial;
  color: #343434;
  padding: 5px;
}
.add-input:focus { 
    outline: none !important;
    border: 2px solid;
    border-color: #088888;
}
.add-icon {
  color: #088888;
  font-size: 28px;
  align-self: center;
  padding-left: 5px;
}
</style>
