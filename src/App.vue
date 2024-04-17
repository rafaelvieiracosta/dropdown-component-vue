<template>
  <div id="app" class="container mx-auto mt-10 px-10">
    <div class="mx-auto mt-20">
      <h3 class="text-lg text-center font-bold mb-4">
        Componente dropdown
      </h3>

      <div class="flex justify-center">
        <DropdownRoot text="Menu">
          <DropdownItem href="https://google.com">Item 1</DropdownItem>
          <DropdownDivider/>
          <DropdownItem href="https://google.com" :to="{ name: 'foo' }">Item 2</DropdownItem>
          <DropdownDivider/>
          <DropdownItem>Item 3</DropdownItem>
        </DropdownRoot>
      </div>
    </div>
  </div>
</template>

<script>
import DropdownRoot from './components/DropdownRoot.vue'
import DropdownItem from './components/DropdownItem.vue'
import DropdownDivider from './components/DropdownDivider.vue'

export default {
  name: 'App',
  components: {
    DropdownRoot,
    DropdownItem,
    DropdownDivider
  }
}
</script>

<style>

</style>
