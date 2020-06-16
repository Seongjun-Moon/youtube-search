<template>
  <div id="app">
    <h1>Youtube Search</h1>
    <SearchBar @input="input" v-model="search" />
    <div id="video">
      <VideoPlayer :afterSearchs="afterSearchs" />
      <VideoList :afterSearchs="afterSearchs" />
    </div>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import VideoPlayer from "./components/VideoPlayer.vue";
import VideoList from "./components/VideoList.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoPlayer,
    VideoList,
  },
  data() {
    return {
      search: "",
      afterSearchs: [],
    };
  },
  methods: {
    input() {
      // 1. 입력된 검색어를 가지고,
      const baseUrl = "https://www.googleapis.com/youtube/v3/search";
      const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY;
      // 2. Youtube API에 요청을 보내어
      axios
        .get(baseUrl, {
          params: {
            // key, part, q
            key: API_KEY,
            part: "snippet",
            type: "video",
            q: this.search,
            maxResults: 10,
          },
        })
        // 'https://www.googleapis.com/youtube/v3/search?part=snippet&q=multicampus&key=AIzaSyBqnr5eUGtFIv-NGzjrvHgCDmx5f10Qurs'
        .then((res) => {
          console.log(res.data);
          this.afterSearchs = res.data.items;
          /* this.afterSearch = res.data.items; */
        });
      // 3. 검색어로 검색한 결과를 가져옴
      console.log("검색어 입력 됨");
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#video {
  display: flex;
}
</style>
