<template>
    <div class="bg-info rounded  p-4 m-2">
        <div class="row">
            <div class="col-12">
                <h3>Name: {{ name }}</h3>
                <p>Email: {{ email }}</p>
                <p>Phone: {{ phone }}</p>
                <p>Is Favorite: {{ isFavorite }}</p>
                <p class="float-end small" v-if="ownername!=''">This contact info belongs to {{ ownername }}</p>
            </div>
        </div>
        
    </div>
</template>

<script setup>
import { ref } from 'vue';
// const email = ref("");
const props = defineProps({ 
    name: { type: String, required: true },
    phone: Number,
    ownername: String,
    email: { type: String,required: false, default: "-n/a-"},
    isFavorite: { type: Boolean, default: false }
});
</script>