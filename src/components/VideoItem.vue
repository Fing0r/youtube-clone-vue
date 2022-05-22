<template>
  <a class="mb-7 group">

    <VideoItemThumbnail :index="index"/>
    <VideoItemInfo :index="index"/>
  </a>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";
import VideoItemThumbnail from "./VideoItemThumbnail.vue";
import VideoItemInfo from "./VideoItemInfo.vue";

export default {
  name: "VideoItem",
  components: {
    VideoItemInfo,
    BaseIcon,
    VideoItemThumbnail
  },
  props: ["index"]
}

</script>

<style scoped>

</style>
