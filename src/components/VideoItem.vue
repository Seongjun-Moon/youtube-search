<template>
  <div>
    <li v-for="afterSearch in afterSearchs" :key="afterSearch.id.videoId">
      <img :src="afterSearch.snippet.thumbnails.default.url" alt="" />

      {{ afterSearch.snippet.title }}
    </li>
  </div>
</template>

<script>
export default {
  name: "VideoItem",
  props: {
    afterSearchs: Array,
  },
};
</script>

<style></style>
