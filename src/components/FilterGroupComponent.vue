<template>
  <div>
    <div class="filter-group mr-12">
          <p>{{ groupName }}</p>
          
          <div class="mt-2 flex flex-col">
            <div v-for="option in options" :key="option.id" class="check">
              <div v-if="optionType==='range'">
                <input type="range" min="1" max="100" value="50">
              </div>
              <div v-else-if="optionType==='checkbox'">
                <input v-on:change="$emit('changed', {group:groupName, checkedNames});" type="checkbox" :id="option.id" :name="option.id" :value="option.id" v-model="checkedNames">
                <label v-bind:for="option.id"> {{ option.name }}</label><br>
              </div>
              <div v-else-if="optionType==='radio'">
                <input v-on:change="$emit('changed', {group:groupName, radioValue})"
                type="radio" :id="option.id" :name="option.id" :value="option.id" v-model="radioValue">
                <label v-bind:for="option.id"> {{ option.name }}</label><br>
              </div>
            </div>
          </div>
        </div>
  </div>
</template>

<script>
export default {
  name: 'FilterGroupComponent',
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
  methods: {
    changed : function() {
      this.$emit('changed', this.radioValue);
    },
  }
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