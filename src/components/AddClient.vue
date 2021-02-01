<template>
  <div>
    <img src="../../src/assets/addclient.png" @click="toggleForm" />
    <div class="modal-mask" v-show="showForm">
      <div class="modal-wrapper">
        <div class="modal-container">
          <h2>Add New Client</h2>
          <form @submit.prevent="addClient">
            <input
              type="text"
              v-model="firstName"
              name="firstName"
              placeholder="First Name"
              required
            />
            <input
              type="text"
              v-model="lastName"
              name="lastName"
              placeholder="Last Name"
            />
            <input
              type="text"
              v-model="address"
              name="address"
              placeholder="Address"
            />
            <input type="number" v-model="age" name="age" placeholder="Age" />
            <input
              type="text"
              v-model="company"
              name="company"
              placeholder="Company"
            />
            <input
              type="text"
              v-model="email"
              name="email"
              placeholder="Email Address"
            />
            <input
              type="text"
              v-model="phone"
              name="phone"
              placeholder="Phone"
            />
            <input type="submit" value="Submit" class="btn" />
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddClient",
  data() {
    return {
      firstName: "",
      lastName: "",
      address: "",
      age: "",
      company: "",
      email: "",
      phone: "",
      showForm: false,
    };
  },
  methods: {
    addClient() {
      const newClient = {
        firstName: this.firstName,
        lastName: this.lastName,
        address: this.address,
        age: this.age,
        company: this.company,
        email: this.email,
        phone: this.phone,
        isActive: true,
        about: "",
      };
      //Send up to parent
      this.$emit("add-client", newClient);
      this.toggleForm();
    },
    toggleForm() {
      this.showForm = !this.showForm;
    },
  },
};
</script>

<style scoped>
form {
  padding-top: 10px;
}

input {
  width: 100%;
  margin-bottom: 5px;
}

.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 300px;
  height: 300px;
  margin: 0px auto;
  padding: 30px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  font-family: Helvetica, Arial, sans-serif;
}
</style>