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
                            <CardsComponent :type="'Clientes'" :percentage="'7%'" :icon="'fa-user'" :qnt="'7950'"></CardsComponent>
                        </div>
                        <div class="col-12 col-md-3">
                            <CardsComponent :type="'Produtos'" :percentage="'10%'" :icon="'fa-box'" :qnt="'37'"></CardsComponent>
                        </div>
                        <div class="col-12 col-md-3">
                            <CardsComponent :type="'Vendas'" :percentage="'7%'" :icon="'fa-store'" :qnt="'120'"></CardsComponent>
                        </div>
                          <div class="col-12 col-md-3">
                            <CardsComponent :type="'Lojas'" :percentage="'3%'" :icon="'fa-chart-pie'" :qnt="'5'"></CardsComponent>
                        </div>
                    </div>
                </div>
                <div class=" mt-5">
                    <div class="row">
                        <div class="col-12 col-md-6">
                            <ListsComponent :users="users"></ListsComponent>
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
            users: [],
        }
    },
    mounted() {
        this.getUsers();
    },
    methods: {
        async getUsers(){
            const response = await axios.get('https://jsonplaceholder.typicode.com/users');
            if(response.status == 200){
                this.users = response.data
                // console.log(response)
            }else{
                console.log("erro na api");
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