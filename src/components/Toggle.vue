<template>
    <label class="switch">
        <input type="checkbox" id="toggle" v-model="toggleStatus" v-on:click="$emit('toggleSlider', !toggleStatus)">
        <span class="slider"></span>
    </label>
</template>

<script>
export default {
  data () {
    return {
      toggleStatus: false,
    }
  },
  emits: ['toggleSlider']
};
</script>

<style scoped>
.switch {
  position: relative;
  display: inline-block;
  width: 52px;
  height: 26px;
}
.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}
.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: .4s;
  transition: .4s;
  border-radius: 26px;
}

.slider:before {
  position: absolute;
  content: "";
  height: 18px;
  width: 18px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: .4s;
  transition: .4s;
  border-radius: 50%;
}

input:checked + .slider {
  background-color: #088888;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196F3;
}

input:checked + .slider:before {
  -webkit-transform: translateX(20px);
  -ms-transform: translateX(20px);
  transform: translateX(20px);
}
</style>