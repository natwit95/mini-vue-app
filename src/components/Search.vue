<template>
  <div class="search-bar">
    <input type="text" v-model="searchTerm" placeholder="Search Client" />
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      searchTerm: "",
    };
  },
  methods: {
    handleSearch() {
      const term = this.searchTerm;
      this.$emit("handle-search", term);
    },
  },
};
</script>

<style scoped>
</style>>

