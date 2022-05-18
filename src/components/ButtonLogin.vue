<template>
  <button
      class="focus:outline-none flex items-center text-sm text-blue-700 uppercase border border-blue-700 rounded-sm">
    <BaseIcon name="userCircle" class="mr-2 w-7 h-7"/>
    Sign In
  </button>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";

export default {
  name: "ButtonLogin",
  components: {BaseIcon}
}
</script>

<style scoped>

</style>
