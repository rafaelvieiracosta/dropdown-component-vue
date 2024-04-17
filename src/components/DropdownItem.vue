<template>
  <component 
    :is="is" 
    :href="href"
    :to="to"
    class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900 cursor-pointer"
  >
    <slot />
  </component>
</template>

<script>
  export default {
    name: 'DropdownItem',
    props: {
      href: {
        type: String,
        default: undefined
      },
      to: {
        type: [String, Object],
        default: undefined
      }
    },
    computed: {
      is () {
        if (typeof this.to !== 'undefined') {
          return 'RouterLink';
        }
        if (typeof this.href !== 'undefined') {
          return 'a';
        }

        return 'button'; 
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>