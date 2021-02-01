<template>
  <div>
    <SearchBar v-on:input="handleSearch"/>
    <AddClient v-on:add-client="addClient"/>
    <ClientsList v-bind:clients="handleSearch(searchTerm)" />
  </div>
</template>

<script>
import axios from "axios";
import ClientsList from "../components/ClientsList";
import AddClient from "../components/AddClient"
import SearchBar from "../components/SearchBar"

export default {
  name: "Home",
  components: {
    ClientsList,
    AddClient,
    SearchBar
  },
  data() {
    return {
      clients: [],
      searchTerm: "",
    };
  },
  methods: {
    addClient(newClient) {
      const {firstName, lastName, address, age, company, email, phone, isActive, about} = newClient
      axios.post('https://next.json-generator.com/api/json/get/N1sIyy_19', { 
        firstName, 
        lastName, 
        address, 
        age, 
        company, 
        email, 
        phone, 
        isActive, 
        about
      })
      .then(resp => this.clients = [...this.clients, JSON.parse(resp.config.data)])
      .catch(err => console.log(err))
    },
     handleSearch(value) {
      this.searchTerm = value
      return this.clients.filter((client) => { 
        return client.lastName.toLowerCase().includes(this.searchTerm.toLowerCase());
      });
    },
  },

  created() {
    axios
      .get("https://next.json-generator.com/api/json/get/N1sIyy_19")
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

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
 