<template>
    <div>
        <DashboardComponent>
            <div slot="slot-pages" class="content-pages">
                <header class="title-pages">
                    <p>Produtos</p>
                </header>


            </div>
        </DashboardComponent>
    </div>
</template>

<script>
import DashboardComponent from '../Dashboard/DashboardComponent'

export default {
    components:{
        DashboardComponent,
    }
}
</script>

<style lang="scss" src="./style.scss" scoped/>