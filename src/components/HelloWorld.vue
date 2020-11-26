<template>
  <div class="container mx-auto py-4">
    <p class="text-4xl">Search and Filter </p>

    <div class="mt-4 p-8 bg-white">
      <div class=" flex items-center input-box">
        <i class="fas fa-search"></i>

        <input type="text" class=" input outline-none px-3 py-1">
      </div>

      <!-- filter -->
      <FilterComponent/>
      <!-- filter -->
    </div>
  </div>
</template>

<script>
import FilterComponent from './FilterComponent';

export default {
  name: 'HelloWorld',
  components: {FilterComponent},
}
</script>

<style scoped>
.input-box{
  width: 250px;
  border: 1px solid gray;
  padding: 2px 10px;
  border-radius: 50px;
}

.input-box input{
  width: 100%;
  padding: 2px 4px;
  margin-left: 8px;
  border-top-right-radius: 50px;
  border-bottom-right-radius: 50px;
  border: 0;
  outline: none;
}

</style>
