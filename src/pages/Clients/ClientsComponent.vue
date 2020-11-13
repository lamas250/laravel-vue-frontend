<template>
    <div>
        
        <DashboardComponent>
          
            <div slot="slot-pages" class="content-pages">
                <header class="title-pages">
                    <p>Clientes</p>
                      <AddClient></AddClient>
                </header>
                <div class="row">
                    <div class="col-12 col-md-12">
                        <Loader v-if='loader'/>
                        <ListaModulo 
                            :data='clients'
                            @onDelete="onDelete"
                        ></ListaModulo>
                    </div>
                </div>


            </div>
        </DashboardComponent>
    </div>
</template>

<script>
import DashboardComponent from '../Dashboard/DashboardComponent'
import ListaModulo from '../../components/ListaModulo'
import Loader from '../../components/Loader'
import AddClient from './AddForm'
const axios = require('axios');

export default {
    name: 'Clients',
       components:{
        DashboardComponent,
        ListaModulo,
        AddClient,
        Loader,
    },
    data() {
        return {
            clients: [],
            loader: false,
        }
    },
    mounted() {
        this.getClients();
    },
    methods: {
        async getClients(){
            this.loader = true;
            const response = await axios.get('/clients');
            if(response.status == 200){
                this.clients = response.data;
                this.loader = false;
            }else{
                console.error(response);
            }
        },
        onDelete(id){
            axios.delete(`/clients/${id}`).then(() => {
                this.getClients();
            })
            .catch(e => {
                alert(e);
            });
        }
    },
 
}
</script>

<style lang="scss" src="./style.scss" scoped/>