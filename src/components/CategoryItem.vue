<template>
  <a href="#" @click="logi" :class="classes">{{ category }}</a>
</template>

<script>

export default {
  name: "CategoryItem",
  props: ["category", "isActive"],
  computed: {
    classes() {
      const classes = ["px-3", "py-1", "transition", "rounded-full", "border"]
      return this.isActive
          ? [...classes, "bg-gray-600", "border-gray-700", "hover:bg-gray-500", "text-white"]
          : [...classes, "bg-gray-100", "border-gray-300", "hover:bg-gray-200"]
    },
    logi() {
      console.log(123)
    }
  },
}

</script>

<style scoped>

</style>
