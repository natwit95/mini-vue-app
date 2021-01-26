<template>
  <div>
    <div v-for="client in clients" v-bind:key="client.id">
      <Client v-bind:client="client" />
    </div>
  </div>
</template>

<script>
import Client from "./Client";

export default {
  name: "ClienstList",
  components: {
    Client,
  },
  props: ["clients"],
};
</script>

<style scoped>

</style>