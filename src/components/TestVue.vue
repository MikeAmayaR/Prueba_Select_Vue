<template>
    <div>
        <select name="select" class="select" v-for="data in products">
            <option
                class="new-color"
                :value="data"
                v-for="dataFinish in data.fruits"
            >
                {{ dataFinish }}
            </option>
        </select>
    </div>
</template>

<script lang="ts">
import axios from "axios";

const baseUrl = import.meta.env.VITE_APP_ENV_FRUTS_URL;
export default {
    data() {
        return { products: null };
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

<style>
select {
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 16px;
    gap: 85px;
    border-color: #f3f3f3;
    position: absolute;
    width: 256px;
    height: 56px;
    left: 32px;
    top: 32px;
    background: #ffffff;
    box-shadow: 0px 10px 15px rgba(35, 78, 82, 0.1);
    border-radius: 8px;
}

.select {
    color: grey;
}

.select option {
    color: black;
}
</style>
