<template>
  <div class="relative inline-block text-left">
    <button
      type="button"
      class="flex items-center justify-center leading-5 transition ease-in-out duration-150 z-50 text-sm font-medium text-gray-600 hover:text-cool-gray-500 active:text-cool-gray-700 focus:outline-none focus:shadow-outline-blue px-4 py-2 bg-white active:bg-gray-50"
      :class="{ 
        'rounded-md' : rounded,
        'border border-cool-gray-300 focus:border-blue-300' : !nacked
      }"
      @click.stop.prevent="toggle()"
    >
      {{ text }}
      <svg
        v-if="!noIcon"
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

    <transition
      enter-active-class="transition ease-out duration-100"
      enter-class="transform opacity-0 scale-95"
      enter-to-class="transform opacity-100 scale-100"
      leave-active-class="transition ease-in duration-75"
      leave-class="transform opacity-100 scale-100"
      leave-to-class="transform opacity-0 scale-95"
    >
      <div 
        v-show="isOpen" 
        class="origin-top-right absolute right-0 mt-2 w-56 shadow-lg z-50 border border-cool-gray-300"
        :class="{ 'rounded-md' : rounded }"
      >
        <div class="py-1 rounded-md bg-white shadow-xs">
          <slot />
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
  export default {
    name: 'DropdownRoot',
    props: {
      text: {
        type: String,
        default: 'Dropdown'
      },
      noIcon: {
        type: Boolean,
        default: false
      },
      rounded: {
        type: Boolean,
        default: false
      },
      nacked: {
        type: Boolean,
        default: false
      }
    },
    data() {
      return {
        isOpen: false
      }
    },
    provide() {
      return {
        dropdown: this,
      }
    },
    watch: {
      isOpen (value) {
        if (value) {
          document.addEventListener('click', this.clickOutListener);
          this.$root.$emit('dropdown::open', this)
        }
      },
    },
    created () {
      this.$root.$on('dropdown::open', this.rootCloseListener);
    },
    methods: {
      toggle () {
        this.isOpen = !this.isOpen;
      },
      close () {
        this.isOpen = false;
        document.removeEventListener('click', this.clickOutListener);
      },
      clickOutListener (evt) {
        if (!this.$el.contains(evt.target)) {
          this.close();
        }
      },
      rootCloseListener (vm) {
        if (vm !== this) {
          this.close();
        }
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>