<template>
  <nav class="flex fixed w-full items-center justify-between h-16 bg-white text-gray-700 border-b border-gray-200 z-10">
  
   <!-- navbar -->

      <button class="h-16 flex items-center justify-center w-16 border-r border-gray-400" aria-label="Open Menu" @click="drawer">

        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"   :d="isOpen ? 'M15 19l-7-7 7-7' : 'M9 5l7 7-7 7'"  />
        </svg>
                
        <!-- <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
        </svg> -->

      </button>

      <button  class="h-16 flex items-center justify-center w-16 border-r border-gray-400" aria-label="Open Menu" @click="showdropdown">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
      </button>

      
<!-- end navbar -->

<aside class="transform top-0 left-0 w-16 mt-16 bg-gray-600 fixed h-full overflow-auto ease-in-out transition-all duration-300 z-30">
      
      <span v-for="(item, index) in items" :key="index" @click="selectedItem(index)" class="flex items-center justify-center p-4 text-white hover:bg-green-200 hover:text-green-500 ">
        <span class="mr-2">
          <svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" class="w-6 h-6">
            <path d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"></path>
          </svg>
        </span>
      </span>
        
    </aside>    
    <aside class="transform mt-16 ml-16 top-0 left-0 w-32 bg-white border-r border-gray-300 fixed h-full overflow-auto ease-in-out transition-all duration-300 z-0"  
     :class="isOpen ? 'translate-x-0' : '-translate-x-full'" 
     >
     <Sidebar :key="componentKey" :subItems="items[selectedIndex].subItems" />
    </aside>
      <div v-if="dropdown" class="right-0 top-0 absolute mt-16 w-56 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 focus:outline-none">
        <div class="py-1" >
          <!-- Active: "bg-gray-100 text-gray-900", Not Active: "text-gray-700" -->
          <a href="#" class="text-gray-700 block px-4 py-2 text-sm" role="menuitem" tabindex="-1" id="menu-item-0">Account settings</a>
          <a href="#" class="text-gray-700 block px-4 py-2 text-sm" role="menuitem" tabindex="-1" id="menu-item-1">Support</a>
          <a href="#" class="text-gray-700 block px-4 py-2 text-sm" role="menuitem" tabindex="-1" id="menu-item-2">License</a>
          <form method="POST" action="#" role="none">
            <button type="submit" class="text-gray-700 block w-full text-left px-4 py-2 text-sm" role="menuitem" tabindex="-1" id="menu-item-3">
              Sign out
            </button>
          </form>
        </div>
      </div>
  </nav>


</template>

<script>

import Sidebar from "./Sidebar.vue";
import Content from './content.vue'
export default {
  data() {
    return {
      items : [
        {
          name : 'Home 1',
          subItems : [
            {name : 'Subitem 1'},{name : 'Subitem 2'},{name : 'Subitem 3'}
            ]
        },
        {
          name : 'Home 2',
           subItems : [
            {name : '2 Subitem 1'},{name : '2 Subitem 2'},{name : '2 Subitem 3'}
          ]
        },
        // {
        //   name : 'Home 3',
        //    subItems : [
        //     {name : '3 Subitem 1'},{name : '3 Subitem 2'},{name : '3 Subitem 3',}
        //   ]
        // },
        ],
         componentKey: 0,
      isOpen: false,
      selectedIndex : 0,
      dropdown : false
  };
  },
  methods: {
    drawer() {
      this.isOpen = !this.isOpen;
    },
    selectedItem(index){
      this.selectedIndex = index;
      console.log('in methods', index)
    },
    showdropdown(){
      this.dropdown = !this.dropdown
    }
  },
  watch: {
    isOpen: {
      immediate: true,
      handler(isOpen) {
        if (process.client) {
          if (isOpen) document.body.style.setProperty("overflow", "hidden");
          else document.body.style.removeProperty("overflow");
        }
      }
    },

        selectedIndex: {
      immediate: true,
      handler(index) {
        if (process.client) {
         this.selectedIndex = index
         console.log('in watch', index)
         this.componentKey += 1;
         // if (isOpen) document.body.style.setProperty("overflow", "hidden");
          // else document.body.style.removeProperty("overflow");
        }
      }
    }
  },
  mounted() {
    document.addEventListener("keydown", e => {
      if (e.keyCode == 27 && this.isOpen) this.isOpen = false;
    });
  },
  computed: {
  },
  components:{
    Sidebar,
    Content
}
};
</script>
