<template>
  <li>
    <a href="#" class="flex items-center px-4 py-2 text-sm hover:bg-gray-100">
      <BaseIcon v-if="iconName"
                :name="iconName"
                class="w-6 h-6 mr-3 text-gray-400"/>
      <span>{{ label }}</span>
      <BaseIcon v-if="withSubMenu"
                name="chevron"
                class="w-5 h-5 text-gray-400 ml-auto"/>
    </a>
  </li>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";

export default {
  name: "DropdownSettingsItem",
  components: {
    BaseIcon
  },
  props: {
    label: String,
    iconName: String,
    withSubMenu: Boolean
  }
}
</script>

<style scoped>

</style>
