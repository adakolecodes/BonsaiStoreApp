<template>
    <div class="container mt-5 mb-5">
        <div class="mb-5">
            <RouterLink to="/">Back Home</RouterLink>
        </div>
        <div v-if="isLoading">Loading...</div>
        <div v-else>
            <div class="row row-cols-1 row-cols-md-4 g-4">
                <div v-for="bonsai in bonsais" :key="bonsai.id" class="card h-100 shadow-sm border-0">
                    <img class="card-img-top" :src="['https://tbhpwebdevapi.azurewebsites.net/' + bonsai.productImage.replace(/^\.\//, '')]" alt="">
                    <div class="card-body">
                        <h5 class="card-title">{{ bonsai.productTitle }}</h5>
                        <h6 class="card-text">${{ bonsai.productPrice }}</h6>
                        <RouterLink :to="`/bonsai/${bonsai.id}`" class="btn btn-dark btn-sm">Details</RouterLink>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'BonsaiView',
    data(){
        return {
            bonsais: [],
            error: '',
            isLoading: true
        }
    },

    async mounted() {
        try {
            const result = await axios.get('https://tbhpwebdevapi.azurewebsites.net/api/BonsaiV2/All');
            console.log(result.data);
            this.bonsais = result.data;
            this.isLoading = false;
        }catch(error) {
            console.log(error);
            this.error = error;
        }
    }
}
</script>

<style scoped>

</style>