<template>
    <div>
        <DashboardComponent>
            <div slot="slot-pages" class="content-pages">
                <header class="title-pages">
                    <p>Produtos</p>
                    <div class="mr-4 mb-2" style="text-align: right;">
                        <Inputs-Create/>
                    </div>
                </header>
                <ListaModulo 
                    :data='products'
                    :columns="['Nome','Preço']"
                 ></ListaModulo>

            </div>
        </DashboardComponent>
    </div>
</template>

<script>
import DashboardComponent from '../Dashboard/DashboardComponent'
import ListaModulo from '../../components/ListaModulo'
import InputsCreate from './Create'
const axios = require('axios');

export default {
    name: 'Products',
    data(){
        return {
            products: [],
        }
    },
    methods: {
        async getProducts(){
            const response = await axios.get('/products');
            if(response.status == 200){
                this.products = response.data;
                console.log(this.products);
            }else{
                console.log('erro');
            }

        }
    },
    mounted() {
        this.getProducts();
    },
    components:{
        DashboardComponent,
        ListaModulo,
        'Inputs-Create': InputsCreate,
    }
}
</script>

<style lang="scss" src="./style.scss" scoped/>