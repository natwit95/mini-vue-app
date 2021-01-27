<template>
  <div>
    <AddClient v-on:add-client="addClient"/>
    <ClientsList v-bind:clients="clients" />
  </div>
</template>

<script>
import axios from "axios";
import ClientsList from "../components/ClientsList";
import AddClient from "../components/AddClient"

export default {
  name: "Home",
  components: {
    ClientsList,
    AddClient
  },
  data() {
    return {
      clients: [],
    };
  },
  methods: {
    addClient(newClient) {
      const {id,firstName, lastName, address, age, company, email, phone, isActive, about} = newClient
      axios.post('https://next.json-generator.com/api/json/get/N1sIyy_19', { 
        id,
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
      .then(resp => this.clients = [...this.clients, resp.data] )
      .catch(err => console.log(err))
    }
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
</style>
 