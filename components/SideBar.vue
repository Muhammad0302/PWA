<template>
    <div>
       <span v-for="(item, index) in lsubItems" :key="index" class="flex items-center p-4 hover:bg-indigo-500 hover:text-white ">
           {{item.name}}
        </span>         
    </div>

</template>

<script>
export default {
  name : 'Sidebar',
  data(){
      return{
                 isOpen: false,
          lsubItems : this.subItems
      }
  },
  props: {
      subItems :{
          type : Array
      }
  },
    methods: {
    drawer() {
      this.isOpen = !this.isOpen;
    }
  },
}
</script>

<style>

</style>