<template>
    <div>
        <DashboardComponent>
            <div slot="slot-pages" class="content-pages">
                <header class="title-pages">
                    <p>Home</p>
                </header>
                <div>
                    <div class="row">
                        <div class="col-12 col-md-3">
                            <CardsComponent :type="'Clientes'" :percentage="'7%'" :icon="'fa-user'" :qnt="clients.length"></CardsComponent>
                        </div>
                        <div class="col-12 col-md-3">
                            <CardsComponent :type="'Produtos'" :percentage="'10%'" :icon="'fa-box'" :qnt="products.length"></CardsComponent>
                        </div>
                        <div class="col-12 col-md-3">
                            <CardsComponent :type="'Vendas'" :percentage="'7%'" :icon="'fa-store'" :qnt="products.length"></CardsComponent>
                        </div>
                          <div class="col-12 col-md-3">
                            <CardsComponent :type="'Lojas'" :percentage="'3%'" :icon="'fa-chart-pie'" :qnt="products.length"></CardsComponent>
                        </div>
                    </div>
                </div>
                <div class=" mt-5">
                    <div class="row">
                        <div class="col-12 col-md-6">
                            <ListsComponent :data="clients" :description="'Clientes'" :columns="['Nome','E-mail']" ></ListsComponent>
                        </div>
                           <div class="col-12 col-md-6">
                            <ListsComponent :data="products" :description="'Produtos'" :columns="['Produto','Valor']" ></ListsComponent>
                        </div>
                    </div>
                </div>
            </div>
        </DashboardComponent>
    </div>
</template>

<script>
import DashboardComponent from '../Dashboard/DashboardComponent'
import CardsComponent from '../../components/CardsComponent'
import ListsComponent from '../../components/ListaComponent'
const axios = require('axios');

export default {
    name: 'HomeComponent',
    data() {
        return {
            clients: [],
            products: [],
        }
    },
    mounted() {
        this.getUsers();
    },
    methods: {
        async getUsers(){
            try {
                const response = await axios.get('/');
                if(response.status == 200){
                    this.clients = response.data.clients;
                    this.products = response.data.products;
                }else{
                    console.error("erro na api");
                }
            }catch (error) {
                console.error(error.response.status);
            }
            
           
        }
    },
    components:{
        DashboardComponent,
        CardsComponent,
        ListsComponent,
    },
}
</script>

<style lang="scss" src="./style.scss" scoped/>