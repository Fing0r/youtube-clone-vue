<template>
  <div class="relative">
    <button @click="dropdownToggle" class="relative p-2 focus:outline-none">
      <BaseIcon name="dotsVertical" class="w-5 h-5"/>
    </button>
    <transition
        enter-active-class="transition ease-out duration-100"
        enter-from-class="transition opacity-0 scale-95"
        enter-to-class="transition opacity-100 scale-100"
        leave-active-class="transition ease-in duration-75"
        leave-from-class="transition opacity-100 scale-100"
        leave-to-class="transition opacity-0 scale-95"
    >
      <div
          tabindex="-1"
          v-show="isOpen"
          ref="dropdown"
          @keydown.esc="dropdownToggle"
          class="absolute top-9 -right-full sm:right-0 bg-white w-72 border border-t-0 focus:outline-none"
      >
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
    </transition>
  </div>
</template>

<script>
import DropdownSettingsItem from "./DropdownSettingsItem.vue";
import BaseIcon from "./BaseIcon.vue";

export default {
  name: "TheDropdownSettings",
  components: {
    BaseIcon,
    DropdownSettingsItem
  },
  data() {
    return {
      isOpen: false,
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
  methods: {
    dropdownToggle() {
      this.isOpen = !this.isOpen
    },
  },
  mounted() {
    window.addEventListener("click", (e) => {
      if (!this.$el.contains(e.target)) {
        this.isOpen = false
      }
    })
  },
  watch: {
    isOpen() {
      this.$nextTick(() => this.isOpen && this.$refs.dropdown.focus());
    }
  },

}
</script>

<style scoped>

</style>
