<template>
    <div class="list">
        <div class="top">
            <p><strong class="mr-3">Clientes</strong><span class="badge badge-info">{{ data.length }}</span></p>
        </div>

        <div class="content">
            <table class="table table-striped">
                <thead>
                    <tr>
                        <th scope="col">#</th>
                        <th scope="col">{{ columns[0] }}</th>
                        <th scope="col">{{ columns[1] }}</th>
                        <th v-if="columns[2]">{{columns[2]}}</th>
                        <th >Ações</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(value, index) in data" :key="value.id">
                        <th scope="row">{{ index + 1 }}</th>
                        <td>{{value.name}}</td>
                        <td>{{ value.price }}</td>
                        <td v-if="columns[2]">{{value.phone }}</td>
                        <td>
                            <button @click.prevent="onEdit(value)" class="btn btn-primary"><i class="fa fa-edit"></i></button>
                            <button @click.prevent="onDelete(value.id)" class="btn btn-danger"><i class="fa fa-trash"></i></button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
  
</template>

<script>
export default {
    name: 'ListaModulo',
    props: {
        data: Array,
        columns: Array,
    },
    methods: {
        onDelete(value){
            this.$emit("onDelete", value);
        },
        onEdit(value){
            this.$emit("onEdit", value);
        }
    },
}
</script>

<style lang="scss" scoped>
.list {
    width: 100%;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #fff;
}
</style>