<template>
  <div
      class="opacity-0 group-hover:opacity-100 absolute top-9 -right-full sm:right-0 bg-white w-72 border border-t-0">
    <section class="py-2 border-b">
      <ul>
        <DropdownSettingsItem
            v-for="item in items.slice(0, 8)"
            :label="item.label"
            :icon-name="item.iconName"
            :withSubMenu="item.withSubMenu"
            :key="item.label"
        />
      </ul>
    </section>
    <section class="py-2">
      <ul>
        <DropdownSettingsItem
            :label="items[8].label"
            :withSubMenu="items[8].withSubMenu"
        />
      </ul>
    </section>
  </div>
</template>

<script>
import DropdownSettingsItem from "./DropdownSettingsItem.vue";

export default {
  name: "TheDropdownSettings",
  components: {
    DropdownSettingsItem
  },
  data() {
    return {
      items: [
        {
          label: "Appearance: Light",
          iconName: "appearance",
          withSubMenu: true
        },
        {
          label: "Language: English",
          iconName: "language",
          withSubMenu: true
        },
        {
          label: "Location: Ukraine",
          iconName: "location",
          withSubMenu: true
        },
        {
          label: "Settings",
          iconName: "settings",
          withSubMenu: false
        },
        {
          label: "Your data in YouTube",
          iconName: "yourData",
          withSubMenu: false
        },
        {
          label: "Help",
          iconName: "help",
          withSubMenu: false
        },
        {
          label: "Send feedback",
          iconName: "feedback",
          withSubMenu: false
        },
        {
          label: "Keyboard shortcuts",
          iconName: "shortcuts",
          withSubMenu: false
        },
        {
          label: "Restricted Mode: Off",
          iconName: null,
          withSubMenu: true
        },
      ]
    }
  },
}
</script>

<style scoped>

</style>
