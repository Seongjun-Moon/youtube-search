<template>
  <div>
    <input type="text" @keypress.enter="input" v-model="search" />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      search: "",
    };
  },
  methods: {
    input() {
      this.$emit("input", this.search);
    },
  },
};
</script>

<style></style>
