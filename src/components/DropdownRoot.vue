<template>
  <div class="relative inline-block text-left">
    <button
      type="button"
      class="flex items-center justify-center leading-5 transition ease-in-out duration-150 z-50 text-sm font-medium text-cool-gray-700 hover:text-cool-gray-500 active:text-cool-gray-700 border border-cool-gray-300 focus:border-blue-300 focus:outline-none focus:shadow-outline-blue rounded px-4 py-2 bg-white active:bg-gray-50"
      @click.stop.prevent="toggle()"
    >
      {{ text }}
      <svg
        class="h-4 w-4 -mr-1 ml-2"
        fill="currentColor"
        viewBox="0 0 20 20"
      >
        <path
          fill-rule="evenodd"
          d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
          clip-rule="evenodd"
        />
      </svg>
    </button>

    <div v-show="isOpen" class="origin-top-right absolute right-0 mt-2 w-56 rounded-md shadow-lg z-50">
      <div class="py-1 rounded-md bg-white shadow-xs">
        <slot />
        <!-- <ul>
          <li class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900 cursor-pointer">
            Opção 1
          </li>

          <li class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900 cursor-pointer">
            Opção 2
          </li>

          <li class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900 cursor-pointer">
            Opção 3
          </li>

          <div class="border-t my-1 border-cool-gray-100" />

          <li class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900 cursor-pointer">
            Opção 4
          </li>

          <li class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900 cursor-pointer">
            Opção 5
          </li>
        </ul> -->
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        isOpen: false
      }
    },
    props: {
      text: {
        type: String,
        default: 'Dropdown'
      },
    },
    methods: {
      toggle () {
        this.isOpen = !this.isOpen;
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>