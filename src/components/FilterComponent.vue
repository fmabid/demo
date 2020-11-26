<template>
  <div class="">
    <div @click="isActive=!isActive"
    class="filter-box rounded-full bg-gray-300 py-2 px-6 mt-8 flex justify-between">
      <span><i class="fas fa-filter"></i> <span class="ml-2">Filter</span></span>
      <span><i class="fas fa-chevron-down"></i></span>
    </div>

    <div class="dropdown-content bg-white py-8 px-8 mt-1 rounded" v-bind:class="{ show: isActive }">
      <div class="flex text-left">
        <CheckBoxGroup
        @changed="onChangeChild"
        :optionType="groups[0].type"
        :options="groups[0].options"
        :groupName="groups[0].name"/>

        <CheckBoxGroup
        @changed="onChangeChild"
        :optionType="groups[1].type"
        :options="groups[1].options"
        :groupName="groups[1].name"/>

        <div>
          <RadioGroup
          @changed="onChangeChild"
          :optionType="groups[2].type"
          :options="groups[2].options"
          :groupName="groups[2].name"/>

          <RadioGroup
          @changed="onChangeChild"
          :optionType="groups[3].type"
          :options="groups[3].options"
          :groupName="groups[3].name"/>
        </div>

        <CheckBoxGroup
        @changed="onChangeChild"
        :optionType="groups[4].type"
        :options="groups[4].options"
        :groupName="groups[4].name"/>

        <CustomRange
        @changed="onChangeChild"
        :optionType="groups[5].type"
        :options="groups[5].options"
        :groupName="groups[5].name"/>
      </div>
      
      <div class="mt-4 float-right">
        <button 
        @click="onApplyFilter"
        class="bg-green-500 text-white font-light py-1 px-4 mx-3 rounded">Apply Filter</button>
        <button class="bg-gray-200 text-black font-light py-1 px-4 mx-3 rounded">Clear</button>
      </div>
    </div>
  </div>
</template>

<script>
import RadioGroup from './RadioGroup';
import CheckBoxGroup from './CheckBoxGroup';
import CustomRange from './CustomRange';

export default {
  name: 'FilterComponent',
  components: {CheckBoxGroup, RadioGroup, CustomRange},
  props: {
    msg: String
  },
  data() {
    return {
      isActive: false,
      groups: [
        {
          name: 'Fleets',
          type: 'checkbox',
          options: [
            {
              id: Math.random(),
              name: 'All fleets ',
            },
            {
              id: Math.random(),
              name: 'Gulshan 1',
            },
            {
              id: Math.random(),
              name: 'Gulshan 2',
            },
            {
              id: Math.random(),
              name: 'Baridhara',
            },
            {
              id: Math.random(),
              name: 'badda',
            },
            {
              id: Math.random(),
              name: 'Rampura',
            },
            {
              id: Math.random(),
              name: 'Mouchak',
            },
            {
              id: Math.random(),
              name: 'Merul',
            },
            {
              id: Math.random(),
              name: 'Linked Road',
            },
          ],
        },
        {
          name: 'Currency',
          type: 'checkbox',
          options: [
            {
              id: Math.random(),
              name: 'All',
            },
            {
              id: Math.random(),
              name: 'USD',
            },
            {
              id: Math.random(),
              name: 'EURO',
            },
            {
              id: Math.random(),
              name: 'USD',
            },
            {
              id: Math.random(),
              name: 'EURO',
            },
          ],
        },
        {
          name: 'Rating',
          type: 'radio',
          options: [
            {
              id: Math.random(),
              name: 'All',
            },
            {
              id: Math.random(),
              name: 'Good',
            },
            {
              id: Math.random(),
              name: 'Bad',
            },
          ],
        },
        {
          name: 'Gender',
          type: 'radio',
          options: [
            {
              id: Math.random(),
              name: 'All',
            },
            {
              id: Math.random(),
              name: 'Male',
            },
            {
              id: Math.random(),
              name: 'Female',
            },
          ],
        },
        {
          name: 'Range',
          type: 'radio',
          options: [
            {
              id: Math.random(),
              name: 'All Range',
            },
            {
              id: Math.random(),
              name: '10 → 20',
            },
            {
              id: Math.random(),
              name: '20 → 30',
            },
            {
              id: Math.random(),
              name: '30 → 40',
            }
          ],
        },
        {
          name: 'Custom Range',
          type: 'range',
        },
      ],
      searchObj: {},
      objArray: [],
    };
  },
  methods: {
    toggleFilterOption: function() {
      this.isActive = !this.isActive;
    },
    onChangeChild: function (value) {
      console.log(value)
      this.searchObj = {...value}

      this.objArray.push(this.searchObj)

      this.$emit('emitedObj', this.objArray)
    },
    onApplyFilter: function() {
      console.log(this.searchObj);
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
