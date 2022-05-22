<template>
  <aside :class="classes">
    <SidebarSection class="none">
      <ul>
        <SidebarCompactNavItem
            v-for="navItem in navItemsData"
            :key="navItem.label"
            :icon="navItem.icon"
            :label="navItem.label"
            :is-active="navItem.isActive"
        />
      </ul>
    </SidebarSection>
  </aside>
</template>

<script>
import SidebarCompactNavItem from "./SidebarCompactNavItem.vue";
import SidebarSection from "./SidebarSection.vue";

export default {
  name: "TheSidebarSmall",
  components: {
    SidebarSection,
    SidebarCompactNavItem
  },
  data() {
    return {
      navItemsData: [
        {
          label: "Home",
          icon: "home",
          isActive: true
        },
        {
          label: "Trending",
          icon: "trending",
          isActive: false
        },
        {
          label: "Subscriptions",
          icon: "subscriptions",
          isActive: false
        },
        {
          label: "Library",
          icon: "library",
          isActive: false
        },
        {
          label: "History",
          icon: "history",
          isActive: false
        },
      ]
    }
  },
  computed: {
    classes() {
      return [
        "min-h-screen",
        "overflow-auto",
        "fixed",
        "top-0",
        "pt-14",
        "bg-white",
        "z-20"
      ]
    }
  },
}
</script>

<style scoped>

</style>
