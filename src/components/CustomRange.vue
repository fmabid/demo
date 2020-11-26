<template>
  <div>
    <p class=" font-bold to-gray-500">{{ groupName }}</p>

    <div class="mt-2 flex flex-col">
      <div class="check">
        <input class="slider" type="range" min="1" max="100" value="50">
        <input class="slider" type="range" min="1" max="100" value="50">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CustomRange',
  props: {
    groupName: String,
    optionType: String,
    options: Array,
  },
}
</script>

<style>
.check{
  margin-top: 5px;
}

.check input[type="range"]{
  width: 100%;
  display: inline;
  float: left;
}

input[type="range"] + input[type="range"]{
  margin-top: -16px;
}

.slider {
  -webkit-appearance: none;
  height: 5px;
  border-radius: 5px;  
  background: #d3d3d3;
  outline: none;
  opacity: 1;
  -webkit-transition: .2s;
  transition: opacity .2s;
}

.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 5px;
  height: 5px;
  border-radius: 50%; 
  background: #4CAF50;
  cursor: pointer;
}

.slider::-moz-range-thumb {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: #4CAF50;
  cursor: pointer;
}

</style>