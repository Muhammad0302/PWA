<template>
<aside class="transform top-0 left-0 w-16 mt-16 bg-gray-600 fixed h-full overflow-auto ease-in-out transition-all duration-300 z-30">
      
      <span v-for="(item, index) in litems" :key="index" class="flex items-center justify-center p-4 text-white hover:bg-green-200 hover:text-green-500 ">
        <span class="mr-2">
          <svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" class="w-6 h-6">
            <path d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"></path>
          </svg>
        </span>
      </span>
        
    </aside>
</template>

<script>
export default {
   data(){
       return {
           litems : this.items
       }
   },
props : {
      items : {
          type : Array
      }
  },
mounted (){
    console.log(this.litems[2].name)
}
}

</script>

<style>

</style>