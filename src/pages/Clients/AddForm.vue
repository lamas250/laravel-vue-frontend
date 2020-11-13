<template>
    <div class="container">
        <form action="">
            <div class="form-row">
                <div class="col-12 col-md-4">
                    <input type="text" class="form-control" placeholder="Nome">
                </div>
                <div class="col-12 col-md-4">
                    <input type="text" class="form-control" placeholder="E-mail">
                </div>
                <div class="col-12 col-md-2">
                    <input type="text" class="form-control" placeholder="Telefone">
                </div>
                <div class="col-12 col-md-1" style="text-align: right;">
                    <button type="submit" class="btn btn-info btn-sm">Criar</button>
                </div>
            </div>
        </form>        
    </div>
</template>

<script>
export default {
    name: 'AddClient',
}
</script>

<style>
.container {
    padding: 10px;
}

</style>