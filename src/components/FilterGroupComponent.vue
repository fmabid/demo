<template>
  <div>
    <div class="filter-group mr-12">
          <p>{{ groupName }}</p>
          
          <div class="mt-2 flex flex-col">
            <div v-for="option in options" :key="option.id" class="check">
              <input :type="optionType" :id="option.id" :name="option.id" value="Bike">
              <label v-bind:for="option.id"> {{ option.name }}</label><br>
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
      opts: Object.assign({}, this.options)
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