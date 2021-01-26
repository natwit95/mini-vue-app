<template>
  <div class="search-bar">
      <input type="text" v-model="test" placeholder="Search Client" @change="handleSearch">
      <label>Search Client</label>
  </div>
</template>

<script>
export default {
    name: 'Search',
    props: ["test"], 
    methods: {
        handleSearch() {
            this.$emit('onchange',this.test)
        }
    }

}
</script>

<style scoped>

</style>>

