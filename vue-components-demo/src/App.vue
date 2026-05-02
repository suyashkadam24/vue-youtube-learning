<template>
    <div class="container">
        <div>{{ message }}</div>
        Contact Owner Name: <input v-model="ownername">
        <div class="row">
            <div class="col-12" v-for="contact in contacts" :key="contact.name">
                <Contact 
                    :name="contact.name" 
                    :phone="contact.phone" 
                    :ownername="contact.ownername" 
                    :email="contact.email" 
                    :isFavorite="contact.isFavorite"
                />
            </div>
        </div>
    </div>
</template>

<script setup> 
import { ref, reactive } from 'vue';
import Contact from './components/Contact.vue';
const message = 'Hello Vue!';
const ownername = ref("Suyash Kadam");
const contacts=reactive([
    { name: "Suyash", phone: 1234567890, ownername: ownername, isFavorite: true },
    { name: "Kadam", phone: 12345654545, ownername: ownername, email: "sk@gmail.com", isFavorite: false },
    {name: "John Doe", phone: 9876543210, ownername: ownername, email: "john@gmail.com", isFavorite: false }
]);
</script>

<style>

</style>