<template>
  <ul>
    <VideoItem :afterSearchs="afterSearchs" />
  </ul>
</template>

<script>
import VideoItem from "../components/VideoItem";

export default {
  name: "VideoList",
  components: {
    VideoItem,
  },
  props: {
    afterSearchs: Array,
  },
};
</script>

<style></style>
