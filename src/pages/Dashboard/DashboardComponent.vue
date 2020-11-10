<template>
    <div class="main">
        <div class="sidebar">
            <SidebarComponent></SidebarComponent>
        </div>

        <div class="content-right">
            <div class="nav">
                <NavbarComponent></NavbarComponent>
            </div>
            <div class="pages">

            </div>
        </div>
    </div>
    
</template>

<script>
import SidebarComponent from "./components/SidebarComponent"
import NavbarComponent from "./components/NavbarComponent"

export default {
    name: 'DashboardComponent', 
    components: {
        SidebarComponent,
        NavbarComponent,
    }  
}
</script>

<style lang="scss" src="./style.scss" scoped/>