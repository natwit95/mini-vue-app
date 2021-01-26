<template>
  <div>
    <Search v-bind:test="search" />
    <ClientsList v-bind:clients="handleSearch" />
  </div>
</template>

<script>
import axios from "axios";
import ClientsList from "../components/ClientsList";
import Search from "../components/Search";

export default {
  name: "Home",
  components: {
    ClientsList,
    Search,
  },
  data() {
    return {
      clients: [],
      search: "",
    };
  },
  methods: {},

  computed: {
    handleSearch() {
      return this.clients.filter((client) => {
        return client.name.first
          .toLowerCase()
          .includes(this.search.toLowerCase());
      });
    },
  },
  created() {
    axios
      .get("https://next.json-generator.com/api/json/get/VkhijADJc")
      .then((res) => (this.clients = res.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
 