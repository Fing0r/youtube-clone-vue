<template>
    <span :class="classes" @mouseenter="toggleBadge" @mouseleave="toggleBadge">
        <BaseIcon :name="icon" class="w-5 h-5"/>
      <span :class="watchClasses">
        <span class="my-1.5 mx-3 inline-block">{{ label }}</span>
      </span>
    </span>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";

export default {
  name: "VideoItemThumbnailButton",
  components: {
    BaseIcon
  },
  data() {
    return {
      isBadgeShown: false
    }
  },
  props: {
    icon: String,
    label: String
  },
  methods: {
    toggleBadge() {
      this.isBadgeShown = !this.isBadgeShown;
    }
  },
  computed: {
    classes() {
      return [
        "opacity-0",
        "group-hover:opacity-100",
        "bg-opacity-60",
        "absolute",
        "right-0",
        "bg-black",
        "text-white",
        "m-1",
        "p-1",
        this.isBadgeShown ? "rounded-r-sm" : "rounded-sm"
      ]
    },
    watchClasses() {
      return [
        "absolute",
        "transition-width",
        "bg-black",
        "bg-opacity-60",
        "whitespace-nowrap",
        "top-0",
        "right-full",
        "overflow-hidden",
        "uppercase",
        "text-xs",
        "delay-100",
        "font-semibold",
        "rounded-l-sm",
        this.isBadgeShown ? "w-28" : "w-0"
      ]
    }
  },
}
</script>

<style scoped>

</style>
