<template>
    <div class="lists">
        <div class="top">
            <p><strong>{{ description }} </strong> <span class="badge badge-info">{{ data.length }}</span></p>
        </div>
        <div class="content">
            <table class="table table-striped my_table">
                <thead>
                    <tr>
                        <th scope="col">#</th>
                        <th scope="col">{{ columns[0] }}</th>
                        <th scope="col">{{ columns[1] }}</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="value in data" :key="value.id">
                        <th scope="row">{{ value.id }}</th>
                        <td>{{value.name}}</td>
                        <td>{{ (description == 'Clientes') ? value.email : value.price }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ListsComponent',
    props: {
        data: Array,
        description: String,
        columns: Array,
    }
}
</script>

<style lang="scss" scoped>
.lists {
    width: 100%;
    padding: 25px;
    border: 1px solid #ccc;
    border-radius: 3px;
    background-color: #fff;


}
</style>