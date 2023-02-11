<template>
    <select name="" id="" v-model="products" v-for="reponses in products" >
        <option :value="reponses">{{ reponses }}</option>
    </select>
</template>

<script lang="ts">
import axios from "axios";
const baseUrl = import.meta.env.VITE_APP_ENV_FRUTS_URL;
console.log('baseUrl', baseUrl)
export default {
    data() {
        return { products: {} };
    },
    mounted() {
        this.getProducts();
    },
    methods: {
        getProducts() {
            axios
                .get(`${baseUrl}`)
                .then((response) => (this.products = response.data));
        },
    },
};
</script>
