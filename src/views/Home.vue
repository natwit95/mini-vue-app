<template>
<div >
  <ClientsList v-bind:clients="clients"/>
</div>

</template>

<script>
import axios from "axios";
import ClientsList from "../components/ClientsList"

export default {
  name: 'Home',
  components: {
    ClientsList
  },
  data() {
    return {
      clients: []
    }
  }, 
  methods: {
    
  },
  created() {
      axios.get('https://next.json-generator.com/api/json/get/VkhijADJc')
      .then(res => this.clients = res.data)
      .catch(err => console.log(err))
    }
  
}
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
</style>
 