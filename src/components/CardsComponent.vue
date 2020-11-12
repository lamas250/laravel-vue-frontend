<template>
    <div class="my_card">
        <div class="content top">
            <h3>{{type}}</h3>
            <p class="percentage"><i class="fa fa-arrow-up"></i>{{percentage}}</p>
        </div>
        <div class="content footer">
            <i :class="['fa', icon]" id="icon"></i>
            <p class="qnt">{{qnt}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardComponent',
    props: {
        type: String,
        percentage: String,
        qnt: Number,
        icon: String

    }
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_main';

.my_card {
    display: flex;
    flex-direction: column;

    background-color: $blue-light;
    padding: 15px;
    border-radius: 7px;
    color: $white;
    box-shadow: 5px 3px 3px black;

    .content {
        display: flex;
        justify-content: space-between;

        #icon {
            font-size: 30px;
        }

        .qnt {
            font-size: 25px;
            margin: 0;
        }
    }

    .percentage {
        color: $orange;
        font-size: 19px;
        font-weight: 900;
    }

   

}
</style>