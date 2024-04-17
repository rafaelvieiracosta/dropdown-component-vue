<template>
  <div id="app" class="flex justify-center items-center mx-auto p-4 min-h-screen">
    <div class="w-full min-h-full max-w-xl">
      <h1 class="text-3xl leading-tall tracking-tight font-medium hyphenated mb-4 text-gray-400">
        _dropdown component with vue
      </h1>

      <div class="flex sm:flex-row flex-col">
        <div class="p-4 border-dashed border border-gray-300 rounded text-solstice-blue group flex-1 m-1">
          <h2 class="mb-4 -mt-2 -mx-1 text-[10px] font-normal leading-loose text-gray-400">
            Default
          </h2>
          
          <div class="mx-auto max-w-fit">
            <DropdownRoot text="Actions">
              <DropdownItem href="https://google.com">Search</DropdownItem>
              <DropdownDivider />
              <DropdownItem :to="{ name: 'foo' }">New Tab</DropdownItem>
              <DropdownItem href="https://google.com" :to="{ name: 'bar' }">New Window</DropdownItem>
              <DropdownDivider />
              <DropdownItem @click="onItem4Click">Show Bookmarks</DropdownItem>
              <DropdownItem>Developer tools</DropdownItem>
            </DropdownRoot>
          </div>
        </div>
      </div>

      <div class="flex sm:flex-row flex-col">
        <div class="p-4 border-dashed border border-gray-300 rounded text-solstice-blue group flex-1 m-1">
          <h2 class="mb-4 -mt-2 -mx-1 text-[10px] font-normal leading-loose text-gray-400">
            Rounded
          </h2>
          
          <div class="mx-auto max-w-fit">
            <DropdownRoot rounded text="Actions">
              <DropdownItem href="https://google.com">Search</DropdownItem>
              <DropdownDivider />
              <DropdownItem :to="{ name: 'foo' }">New Tab</DropdownItem>
              <DropdownItem href="https://google.com" :to="{ name: 'bar' }">New Window</DropdownItem>
              <DropdownDivider />
              <DropdownItem @click="onItem4Click">Show Bookmarks</DropdownItem>
              <DropdownItem>Developer tools</DropdownItem>
            </DropdownRoot>
          </div>
        </div>

        <div class="p-4 border-dashed border border-gray-300 rounded text-solstice-blue group flex-1 m-1">
          <h2 class="mb-4 -mt-2 -mx-1 text-[10px] font-normal leading-loose text-gray-400">
            No icon
          </h2>
          
          <div class="mx-auto max-w-fit">
            <DropdownRoot no-icon text="Actions">
              <DropdownItem href="https://google.com">Search</DropdownItem>
              <DropdownDivider />
              <DropdownItem :to="{ name: 'foo' }">New Tab</DropdownItem>
              <DropdownItem href="https://google.com" :to="{ name: 'bar' }">New Window</DropdownItem>
              <DropdownDivider />
              <DropdownItem @click="onItem4Click">Show Bookmarks</DropdownItem>
              <DropdownItem>Developer tools</DropdownItem>
            </DropdownRoot>
          </div>
        </div>

        <div class="p-4 border-dashed border border-gray-300 rounded text-solstice-blue group flex-1 m-1">
          <h2 class="mb-4 -mt-2 -mx-1 text-[10px] font-normal leading-loose text-gray-400">
            Nacked
          </h2>
          
          <div class="mx-auto max-w-fit">
            <DropdownRoot nacked text="Actions">
              <DropdownItem href="https://google.com">Search</DropdownItem>
              <DropdownDivider />
              <DropdownItem :to="{ name: 'foo' }">New Tab</DropdownItem>
              <DropdownItem href="https://google.com" :to="{ name: 'bar' }">New Window</DropdownItem>
              <DropdownDivider />
              <DropdownItem @click="onItem4Click">Show Bookmarks</DropdownItem>
              <DropdownItem>Developer tools</DropdownItem>
            </DropdownRoot>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import DropdownRoot from "./components/DropdownRoot.vue";
import DropdownItem from "./components/DropdownItem.vue";
import DropdownDivider from "./components/DropdownDivider.vue";

export default {
  name: "App",
  components: {
    DropdownRoot,
    DropdownItem,
    DropdownDivider,
  },
  methods: {
    onItem4Click(evt) {
      console.log("OISS", evt);
    },
  },
};
</script>

<style>
body {
  @apply bg-gray-100;
}
</style>
