<template>
    <div>
        
        <DashboardComponent>
          
            <div slot="slot-pages" class="content-pages">
                <header class="title-pages">
                    <p>Clientes</p>
                        <AddClient 
                            :form="form"
                            @onFormSubmit="onFormSubmit"
                        ></AddClient>
                </header>
                <div class="row">
                    <div class="col-12 col-md-12">
                        <Loader v-if='loader'/>
                        <ListaModulo 
                            :data='clients'
                            :columns="['Nome','E-mail','Telefone']"
                            @onDelete="onDelete"
                            @onEdit="onEdit"
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
            form: {name: '', email: '', phone: '',isEdit: false},
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
        },
        onEdit(data){
            this.form = data;
            this.form.isEdit = true;
        },
        editClient(data){
            axios.put(`/clients/${data.id}`,{
                name: data.name,
                email: data.email,
                phone: data.phone
            }).then(() => {
                this.getClients();
            }).catch(e => {
                alert(e);
            })
        },
        onFormSubmit(data){
            // console.log(data.isEdit);
            if(data.isEdit){
                // call edit client
                // console.log(data.name);
                this.editClient(data);
            }else{
                // call create client
                axios.post('/clients/store',{
                    name: data.name,
                    email: data.email,
                    phone: data.phone
                }).then(() => {
                    this.getClients();
                }).catch(e => {
                    alert(e);
                });
            }
        },
        
    },
 
}
</script>

<style lang="scss" src="./style.scss" scoped/>