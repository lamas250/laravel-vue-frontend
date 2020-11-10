<template>
    <div class="sidebar">
        <div class="top">
            <div class="avatar">
                <span><i class="fa fa-user"></i></span>
            </div>
            <div class="info">
                <p>Igor Lamas</p>
                <span>Online</span>
            </div>
        </div>
        <div class="menu">
            <ul>
                <li><router-link :to="{name:'home'}"><i class="fa fa-home"></i> Início</router-link></li>
                <li><router-link :to="{name:'products'}"><i class="fa fa-box"></i> Produtos</router-link></li>
                <li><router-link :to="{name:'home'}"><i class="fa fa-store"></i> Vendas</router-link></li>
                <li><router-link :to="{name:'home'}"><i class="fa fa-chart-bar"></i> Relatório</router-link></li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SidebarComponent',
}
</script>

<style lang="scss">

.sidebar {

    .top {
        width: 100%;
        color: #fff;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 25px 5px;
        margin-top: 25px;
        
        .avatar {
            margin-right: 10px;
            width: 70px;
            height: 70px;
            border-radius: 50%;
            background-color: silver;

            display: flex;
            justify-content: center;
            align-items: center;

            font-size: 30px;
        }

        .info {
            p {
                margin: 0px;
            }

            span {
              font-size: 11px;  
            }
        }
    }

    .menu {
        padding: 10px;
        margin-left: 20px;
        margin-top: 30px;

        ul, li {
            margin: 15px 0;
            font-size: 17px;
            list-style: none;
            font-weight: 200;
            a {
                color:#fff;
                text-decoration: none;
            }
        }
    }
}

</style>