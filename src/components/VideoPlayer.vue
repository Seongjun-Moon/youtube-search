<template>
  <div v-if="afterSearchs.length > 0">
    <iframe
      :src="`https://www.youtube.com/embed/${afterSearchs[0].id.videoId}`"
      frameborder="0"
      width="500"
      height="500"
    ></iframe>
  </div>
</template>

<script>
export default {
  name: "VideoPlayer",
  props: {
    afterSearchs: Array,
  },
};
</script>

<style></style>
