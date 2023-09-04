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
    name: 'BonsaiCategoryView',
    data() {
        return {
            bonsais: [],
            error: '',
            isLoading: true
        }
    },
    async created() {
        this.fetchBonsaisForCategory(this.$route.params.category); // Initial fetch based on the route parameter
    },
    watch: {
        '$route.params.category': 'fetchBonsaisForCategory' // Watch for changes to the route parameter
    },
    methods: {
        async fetchBonsaisForCategory(category) {
            try {
                const categoryResponse = await axios.get(`https://tbhpwebdevapi.azurewebsites.net/api/BonsaiV2/Category?category=${category}`);
                const categoryBonsaiIds = categoryResponse.data; // Assuming this API returns an array of bonsai ids for the given category

                const bonsaisResponse = await axios.get('https://tbhpwebdevapi.azurewebsites.net/api/BonsaiV2/All');
                const allBonsais = bonsaisResponse.data; // Assuming this API returns an array of all bonsais

                // Filter bonsais based on the ids from the category response
                this.bonsais = allBonsais.filter(bonsai => categoryBonsaiIds.includes(bonsai.id));
                this.isLoading = false;
            } catch (error) {
                console.log(error);
                this.error = error;
            }
        }
    }
}

// import axios from 'axios'

// export default {
//     name: 'BonsaiCategoryView',
//     data() {
//         return {
//             bonsais: [],
//             error: '',
//             isLoading: true
//         }
//     },
//     async mounted() {
//         try {
//             const category = this.$route.params.category; // Fetch the category from the route parameter
//             const categoryResponse = await axios.get(`https://tbhpwebdevapi.azurewebsites.net/api/BonsaiV2/Category?category=${category}`);
//             const categoryBonsaiIds = categoryResponse.data; // Assuming this API returns an array of bonsai ids for the given category

//             const bonsaisResponse = await axios.get('https://tbhpwebdevapi.azurewebsites.net/api/BonsaiV2/All');
//             const allBonsais = bonsaisResponse.data; // Assuming this API returns an array of all bonsais

//             // Filter bonsais based on the ids from the category response
//             this.bonsais = allBonsais.filter(bonsai => categoryBonsaiIds.includes(bonsai.id));
//             this.isLoading = false;
//         } catch (error) {
//             console.log(error);
//             this.error = error;
//         }
//     }
// }
</script>
  
<style scoped>

</style>
  