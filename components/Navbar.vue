<template>
  <nav
    class="flex fixed w-full items-center justify-between px-6 h-16 bg-white text-gray-700 border-b border-gray-200 z-10"  >

    <aside
      class="transform top-0 left-0 w-24 bg-white fixed h-full overflow-auto ease-in-out transition-all duration-300 z-30"
     >
      <span
        class="flex w-full items-center h-16 p-4 border-b"
      >
        <img src="../static/fox-hub.png" alt="Logo" class="h-auto w-32 mx-auto" />
      </span>
      
      <span
        class="flex items-center p-4 hover:bg-indigo-500 hover:text-white "
        ><span class="mr-2">
          <svg
            fill="none"
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            viewBox="0 0 24 24"
            class="w-12 h-12"
          >
            <path
              d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"
            ></path>
          </svg>
        </span>
        </span>
      
    </aside>
  </nav>
</template>

<script>
export default {
  data() {
    return {
    };
  },
  methods: {
  },
  watch: {
  },
  mounted() {
  }
};
</script>
