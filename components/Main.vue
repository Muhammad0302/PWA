<template>
<div class="flex">
 <!-- left side -->
  <div class="h-screen overflow-y-scroll top-0 sticky">
    <!-- Note: add overflow-y-scroll if sidebar content is longer than page -->
   <Home />
  </div>
  <!-- right side -->
  <div class="flex-grow w-full ml-16 p-4 bg-gray-100">   
    <Content />

  </div>

</div>
</template>

<script>
import Home from './Home.vue'
import Content from './content.vue'
export default {

components :{
    Home, Content
}
}
</script>

<style>

</style>