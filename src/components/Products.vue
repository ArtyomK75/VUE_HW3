<template>
    <div>
        <h1>Products</h1>
        <v-container>
            <v-row>
                <v-col v-for="product in items" :key="product.id">
                    <product :product="product"/>
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>

<script>
    import axiosInstance from "../../services/axios";
    import Product from "@/components/Product.vue";

    export default {
        name: 'Products',
        components: {
            Product,
        },        
        data () {
            return {
                items: [],
            }
        },        methods: {
            async getProducts() {
                try {
                    const response = await axiosInstance.get('/products');
                    this.items = response.data;
                } catch (error) {
                    console.log(error);                
                }
            }
        },
        mounted() {
            this.getProducts();
        }

    };
</script>


