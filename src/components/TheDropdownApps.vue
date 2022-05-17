<template>
  <div class="opacity-0 group-hover:opacity-100 absolute top-9 right-0 sm:left-0 bg-white w-60 border border-t-0">
    <section class="py-2 border-b">
      <ul>
        <DropdownAppsItem label="YouTube TV"/>
      </ul>
    </section>
    <section class="py-2 border-b">
      <ul>
        <DropdownAppsItem label="YouTube Music"/>
        <DropdownAppsItem label="YouTube Kids"/>
      </ul>
    </section>
    <section class="py-2">
      <ul>
        <DropdownAppsItem label="Creator Academy"/>
        <DropdownAppsItem label="YouTube for Artists"/>
      </ul>
    </section>
  </div>
</template>

<script>
import DropdownAppsItem from "./DropdownAppsItem.vue";

export default {
  name: "TheDropdownApps",
  components: {
    DropdownAppsItem
  }
}
</script>

<style scoped>

</style>
