<template>
  <TheSearchInput/>
  <TheSearchButton/>
</template>

<script>
import TheSearchInput from "./TheSearchInput.vue";
import TheSearchButton from "./TheSearchButton.vue";

export default {
  name: "TheSearch",
  components: {
    TheSearchButton,
    TheSearchInput
  }
}
</script>

<style scoped>

</style>
