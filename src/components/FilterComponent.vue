<template>
  <div>
    <div class="filter-box rounded-full bg-gray-300 py-2 px-6 mt-8 flex justify-between">
      <span><i class="fas fa-filter"></i> <span class="ml-2">Filter</span></span>
      <span><i class="fas fa-chevron-down"></i></span>
    </div>
    <div class="dropdown-content bg-white py-8 px-8 mt-1 rounded">
      <div class="flex text-left">
        <FilterGroupComponent 
        v-for="item in groups" 
        :key="item.id"
        :optionType="item.type"
        :options="item.options"
        :groupName="item.name"/>
      </div>
      
      <div class="mt-4 float-right">
        <button class="bg-green-500 text-white font-light py-1 px-4 mx-3 rounded">Apply Filter</button>
        <button class="bg-gray-200 text-black font-light py-1 px-4 mx-3 rounded">Clear</button>
      </div>
    </div>
  </div>
</template>

<script>
import FilterGroupComponent from './FilterGroupComponent';

export default {
  name: 'FilterComponent',
  components: {FilterGroupComponent},
  props: {
    msg: String
  },
  data() {
    return {
      groups: [
        {
          name: 'Fleets',
          type: 'checkbox',
          options: [
            {
              id: Math.random(),
              name: 'Opt 1',
            },
            {
              id: Math.random(),
              name: 'Opt 2',
            },
            {
              id: Math.random(),
              name: 'Opt 3',
            },
            {
              id: Math.random(),
              name: 'Opt 4',
            },
          ],
        },
        {
          name: 'Currency',
          type: 'checkbox',
          options: [
            {
              id: Math.random(),
              name: 'Opt 1',
            },
            {
              id: Math.random(),
              name: 'Opt 2',
            }
          ],
        },
        {
          name: 'Rating',
          type: 'radio',
          options: [
            {
              id: Math.random(),
              name: 'Opt 1',
            },
            {
              id: Math.random(),
              name: 'Opt 2',
            }
          ],
        },
        {
          name: 'Custom Range',
          type: 'range',
        },
      ],
    };
  },
  methods: {
    toggleFilterOption: function() {

    }
  }
}
</script>


<style scoped>
/* filter */

.filter-box{
  width: 200px;
  cursor: pointer;
}

.dropdown-content {
  position: absolute;
  min-width: 160px;
  overflow: auto;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 100;
}
</style>
