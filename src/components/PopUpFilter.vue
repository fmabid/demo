<template>
  <div>
    <div @mouseover="isActive=true" @mouseleave="isActive=false" 
     class="popup-filter rounded-full bg-gray-300 py-2 px-4 mt-8 mx-4 flex items-center justify-between hover:bg-white hover:shadow-md">
      <span class="mr-4">{{ group }}</span>
      <i class="fas fa-times"></i>
    </div>
    <div class="dropdown-content bg-white py-8 px-8 mt-1 rounded" v-bind:class="{ show: isActive }">
      jknk
    </div>
  </div>
</template>

<script>
export default {
name: 'PopUpFilter',
props: {
    group: {},
  },
data() {
    return {
      isActive: false,
    };
  },
}
</script>

<style>
.popup-filter i:hover{
  cursor: pointer;
}

.popup-filter i{
  font-size: 10px;
  color: white;
  padding: 3px 5px;
  border-radius: 10px;
  background-color: black;

}

.dropdown-content {
  display: none;
  position: absolute;
  min-width: 160px;
  overflow: auto;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 100;
}

.show{
  display: block;
}
</style>