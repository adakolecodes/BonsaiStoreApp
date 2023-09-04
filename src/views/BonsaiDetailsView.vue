<template>
    <div class="container mt-5 mb-5">
        <!-- <div class="mb-5">
            <router-link to="/bonsai" class="btn btn-link">Back</router-link>
        </div> -->
        <div v-if="isLoading">Loading...</div>
        <div v-else>
            <div class="row">
                <div class="col-md-4">
                    <img :src="['https://tbhpwebdevapi.azurewebsites.net/' + queryBonsai.productImage.replace(/^\.\//, '')]" alt="" class="img-fluid">
                </div>
                <div class="col-md-8">
                    <h1>{{ queryBonsai.productTitle }}</h1>
                    <h5>{{ queryBonsai.productPrice }}</h5>
                    <p>{{ queryBonsai.productDescription }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import axios from 'axios'
import {ref, onMounted} from 'vue'
import { useRoute } from 'vue-router';

const queryBonsai = ref({});
const isLoading = ref(true);
const route = useRoute();

onMounted(async () => {
    try{
        const result = await axios.get(`https://tbhpwebdevapi.azurewebsites.net/api/BonsaiV2/${route.params.id}`);
        console.log(result.data);
        queryBonsai.value = result.data;
        isLoading.value = false;
    }catch(error){
        console.log(error);
    }
})
</script>

<style scoped>

</style>