<template>
  <div class="filter-group mr-12">
    <p class=" font-bold text-gray-700">{{ groupName }}</p>

    <div class="mt-2 flex flex-col">
      <div v-for="option in options" :key="option.id" class="check">
        <input v-on:change="$emit('changed', {group:groupName, checkedNames});"
         type="checkbox" :id="option.id" :name="option.id" :value="option.id" v-model="checkedNames">
        <label v-bind:for="option.id"> {{ option.name }}</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name:'CheckBoxGroup',
  props: {
    groupName: String,
    optionType: String,
    options: Array,
  },
  data() {
    return {
      checkedNames: [],
      radioValue: '',
      range: '',
    };
  },
}
</script>

<style>
.filter-group {
  color: black;
  padding: 12px 16px;
  padding-left: 0;
  text-decoration: none;
  display: block;
}

.check{
  margin-top: 5px;
}

input[type="checkbox"] {
  visibility: hidden;
}

input[type="checkbox"] + label:before {
  border: 1px solid #333;
  content: "\00a0";
  display: inline-block;
  font: 12px/1em sans-serif;
  height: 16px;
  margin: 0 .25em 0 -15px;
  vertical-align: top;
  width: 16px;
  border-radius: 3px;
}

input[type="checkbox"]:checked + label:before {
  background: black;
  color: #333;
  content: "\00a0";
  text-align: center;
  border-radius: 3px;
  border: 1px solid #333;
}
input[type="checkbox"]:checked + label:after {
  font-weight: bold;
  border-radius: 3px;
}


</style>