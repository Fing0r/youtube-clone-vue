<template>
  <div class="relative">
    <button
        @click="dropdownToggle"
        class="relative p-2 focus:outline-none">
      <BaseIcon name="viewGrid" class="w-5 h-5"/>
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
          class="absolute top-9 right-0 bg-white w-60 border border-t-0 focus:outline-none"
      >
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
    </transition>
  </div>
</template>

<script>
import DropdownAppsItem from "./DropdownAppsItem.vue";
import BaseIcon from "./BaseIcon.vue";

export default {
  name: "TheDropdownApps",
  data() {
    return {
      isOpen: false
    }
  },
  components: {
    BaseIcon,
    DropdownAppsItem
  },
  methods: {
    dropdownToggle() {
      this.isOpen = !this.isOpen
    }
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
