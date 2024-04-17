<template>
  <component
    :is="is"
    :href="localHref"
    :to="to"
    class="block flex items-center w-full px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900 cursor-pointer"
    @click="onClick"
  >
    <div class="flex items-center justify-between flex-wrap grow">
      <span class="inline-block leading-loose text-gray-700">
        <slot />
      </span>
      <span class="flex items-center p-1 text-[10px] uppercase leading-none font-semibold text-white bg-gray-400 no-underline rounded whitespace-no-wrap">
        {{  mappingIs[is] }}
      </span>
    </div>
  </component>
</template>

<script>
export default {
  name: "DropdownItem",
  inject: ["dropdown"],
  props: {
    href: {
      type: String,
      default: undefined,
    },
    to: {
      type: [String, Object],
      default: undefined,
    },
  },
  data() {
    return {
      mappingIs: {
        'RouterLink': 'router',
        'a': 'href',
        'button': 'button'
      }
    }
  },
  computed: {
    localHref() {
      if (typeof this.to !== "undefined") {
        return undefined;
      }

      return this.href;
    },
    is() {
      if (typeof this.to !== "undefined") {
        return "RouterLink";
      }
      if (typeof this.href !== "undefined") {
        return "a";
      }

      return "button";
    },
  },
  methods: {
    onClick(evt) {
      this.$emit("click", evt);
      this.closeDropdown();
    },
    closeDropdown() {
      this.dropdown.close();
    },
  },
};
</script>

<style lang="scss" scoped></style>
