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
                            <CardsComponent></CardsComponent>
                        </div>
                        <div class="col-12 col-md-3">
                            <CardsComponent></CardsComponent>
                        </div>
                          <div class="col-12 col-md-3">
                            <CardsComponent></CardsComponent>
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

export default {
    components:{
        DashboardComponent,
        CardsComponent,
    },
    data(){

    }
}
</script>

<style lang="scss" src="./style.scss" scoped/>