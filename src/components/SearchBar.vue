 <template>
  <div>
    <label>Search Client</label><br>
    <input
      type="text"
      v-model="searchTerm"
      placeholder="🔍 Search By Last Name"
      @input="handleSearch"
      class="search-bar"
    />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      searchTerm: "",
    };
  },
  methods: {
    handleSearch() {
      this.$emit("input", this.searchTerm);
    },
  },
};
</script>

<style scoped>
.search-bar {
  padding: 10px;
  width: 100%;
}
</style>>
