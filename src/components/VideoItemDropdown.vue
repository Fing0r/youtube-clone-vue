<template>
  <div class="relative -mt-1 ml-auto">
    <button @click="dropdownToggle" :class="buttonClasses">
      <BaseIcon name="dotsVertical"/>
    </button>

    <transition
        enter-active-class="transition ease-out duration-100"
        enter-from-class="transition opacity-0 scale-95"
        enter-to-class="transform opacity-100 scale-100"
        leave-active-class="transition ease-in duration-75"
        leave-from-class="transform opacity-100 scale-100"
        leave-to-class="transform opacity-0 scale-95"
    >
      <div
          tabindex="-1"
          v-show="isOpen"
          ref="dropdown"
          @keydown.esc="dropdownToggle"
          :class="dropdownClasses"
      >
        <section class="py-2">
          <ul>
            <VideoItemDropdownListItem
                label="Add to queue"
                icon="menuAlt3"
            />
          </ul>
        </section>
      </div>
    </transition>
  </div>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";
import VideoItemDropdownListItem from "./VideoItemDropdownListItem.vue";

export default {
  name: "VideoItemDropdown",
  components: {
    BaseIcon,
    VideoItemDropdownListItem
  },
  data() {
    return {
      isOpen: false,
      positionClasses: []
    }
  },
  methods: {
    dropdownToggle(e) {
      this.isOpen = !this.isOpen;

      if (this.isOpen) {
        this.$nextTick(() => {
          this.positionClasses = this.getPositionClasses(e);
        })
      }
    },
    getPositionClasses(e) {
      return [
        this.getTopClass(e),
        this.getRightClass(e),
        this.getLeftClass(e)
      ]
    },
    getTopClass(e) {
      const dropdownBtnHeight = e.currentTarget.offsetHeight;
      const clickCoordY = e.clientY;
      const dropdownHeight = this.$refs.dropdown.offsetHeight;

      const isDropdownBottom = window.innerHeight - clickCoordY < dropdownHeight;
      // window.innerHeight - clickCoordY < dropdownBtnHeight + dropdownHeight

      if (window.innerHeight - clickCoordY < 52) {
        return '-top-14'
      }

      if (window.innerHeight - clickCoordY < 84) {
        return 'top-0'
      }

      return 'top-9'
    },
    getRightClass(e) {
      const clickCoordX = e.clientX;
      const dropdownWidth = this.$refs.dropdown.offsetWidth;
      const clickCoordY = e.clientY;

      if (window.innerWidth - clickCoordX > dropdownWidth) {
        return "right-auto"
      }

      if (window.innerHeight - clickCoordY > 84) {
        return 'right-0'
      }

      if (window.innerHeight - clickCoordY > 52) {
        return 'right-8'
      }

      return "right-0"

    },
    getLeftClass(e) {
      const clickCoordX = e.clientX;
      const dropdownWidth = this.$refs.dropdown.offsetWidth;
      const clickCoordY = e.clientY;

      if (window.innerHeight - clickCoordY > 84) {
        return 'left-auto'
      }

      if ((window.innerHeight - clickCoordY > 52) && (window.innerWidth - clickCoordX > dropdownWidth)) {
        return 'left-8'
      }

      return "left-auto"
    }
  },
  mounted() {
    window.addEventListener("click", (e) => {
      if (!this.$el.contains(e.target)) {
        this.isOpen = false
      }
    })
  },
  computed: {
    buttonClasses() {
      return [
        "-mt-1",
        "ml-auto",
        "p-1",
        "opacity-0",
        "group-hover:opacity-100",
        "text-gray-500",
        "hover:text-gray-700",
        "focus:outline-none"
      ]
    },
    dropdownClasses() {
      return [
        "z-10",
        "absolute",
        // "-right-full",
        // "sm:right-0",
        "bg-white",
        "w-48",
        "rounded",
        "shadow",
        "focus:outline-none",
        ...this.positionClasses,
      ]
    }
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
