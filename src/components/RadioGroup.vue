<template>
  <div class="filter-group mr-12">
    <p class=" font-bold text-gray-700">{{ groupName }}</p>

    <div class="mt-2 flex flex-col">
      <div v-for="option in options" :key="option.id" class="check">
        <input v-on:change="$emit('changed', {group:groupName, radioValue})"
          type="radio" :id="option.id" :name="option.id" :value="option.id" v-model="radioValue">
        <label v-bind:for="option.id"> {{ option.name }}</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name:'RadioGroup',
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
</style>
