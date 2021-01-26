<template>
  <div class="client-item">
    <h2>
      {{ client.name.first }} {{ client.name.last }}
      <button v-on:click="showMore" class="show-more">{{showInfo ? '˄' : '˅'}} </button>
    </h2>
    <div class="client-info" v-if="showInfo">
      <table>
        <tr>
          <th scope="col">Address</th>
          <th scope="col">Age</th>
          <th scope="col">Company</th>
          <th scope="col">Email</th>
          <th scope="col">Phone</th>
        </tr>
        <tr>
          <td>{{ client.address }}</td>
          <td>{{ client.age }}</td>
          <td>{{ client.company }}</td>
          <td>{{ client.email }}</td>
          <td>{{ client.phone }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "Client",
  data() {
    return {
      showInfo: false,
    };
  },
  props: ["client"],
  methods: {
    showMore() {
      this.showInfo = !this.showInfo;
    },
  },
};
</script>

<style scoped>
.client-item {
  background: #f1ebeb;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
.show-more {
  background: #5a5858;
  color: #ffffff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}

table {
  border-collapse: collapse;
  width: 100%;
}
th,
td {
  border: 1px solid #cecfd5;
  padding: 10px 15px;
}
</style>