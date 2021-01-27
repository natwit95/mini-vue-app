<template>
    <div class="client-form">
        <form @submit="addClient">
            <input type="text" v-model="firstName" name="firstName" placeholder="First Name">
            <input type="text" v-model="lastName" name="lastName" placeholder="Last Name">
            <input type="text" v-model="address" name="address" placeholder="Address">
            <input type="number" v-model="age" name="age" placeholder="Age">
            <input type="text" v-model="company" name="company" placeholder="Company">
            <input type="text" v-model="email" name="email" placeholder="Email Address">
            <input type="text" v-model="phone" name="phone" placeholder="Phone">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>

export default {
    name: "AddClient",
    data() {
        return {
            id: 1,
            firstName: '',
            lastName: '',
            address: '',
            age: "",
            company: "",
            email: '',
            phone: '',
            
        }
    },
    methods: {
        addClient(e) {
            e.preventDefault()
            const newClient = {
                id: this.id,
                firstName: this.firstName,
                lastName: this.lastName,
                address: this.address,
                age: this.age,
                company: this.company,
                email: this.email,
                phone: this.phone,
                isActive: true,
                about: ""
            }
            //Send up to parent
            this.$emit('add-client', newClient)

        }
    }
}
</script>

<style scoped>

    form {
        display: flex;
    }
    
    input[type='text'] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 4;
    }

</style>