<template>
  <TheHeader @toggle-sidebar="toggleSidebar"/>
  <TheSidebarCompact v-if="isCompactSidebarOpen"/>
  <TheSidebar v-if="isNormalSidebarOpen"/>
  <TheSidebarMobile
      :is-open="isMobileSidebarOpen"
      @close="closeMobileSidebar"/>
  <TheCategories :is-sidebar-open="isNormalSidebarOpen"/>
  <TheVideos :is-sidebar-open="isNormalSidebarOpen"/>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import TheSidebarCompact from "./components/TheSidebarCompact.vue";
import TheSidebar from "./components/TheSidebar.vue";
import TheSidebarMobile from "./components/TheSidebarMobile.vue";
import TheCategories from "./components/TheCategories.vue";
import TheVideos from "./components/TheVideos.vue";

export default {
  components: {
    TheVideos,
    TheCategories,
    TheSidebarMobile,
    TheSidebar,
    TheSidebarCompact,
    TheHeader
  },
  data() {
    return {
      isMobileSidebarOpen: false,
      isCompactSidebarOpen: false,
      isNormalSidebarOpen: false,
      isCompactSidebarActive: false
    }
  },
  methods: {
    toggleSidebar() {
      if (window.innerWidth >= 1280){
        this.isCompactSidebarActive = !this.isCompactSidebarActive;
        this.onResize();
      } else {
        this.openMobileSidebar();
      }
    },
    onResize() {
      if (window.innerWidth < 768) {
        this.isCompactSidebarOpen = false;
        this.isNormalSidebarOpen = false;
      } else if (window.innerWidth < 1280) {
        this.isCompactSidebarOpen = true;
        this.isNormalSidebarOpen = false;
      } else {
        this.isCompactSidebarOpen = this.isCompactSidebarActive;
        this.isNormalSidebarOpen = !this.isCompactSidebarActive;
        this.isMobileSidebarOpen = false;
      }
    },

    openMobileSidebar() {
    this.isMobileSidebarOpen = true;
    },
    closeMobileSidebar() {
    this.isMobileSidebarOpen = false;
    },
  },
  mounted() {
    this.onResize();
    window.addEventListener('resize', this.onResize);
  },
}
</script>

<style>

html::-webkit-scrollbar,
aside::-webkit-scrollbar,
div::-webkit-scrollbar {
  display: none;
}
</style>
