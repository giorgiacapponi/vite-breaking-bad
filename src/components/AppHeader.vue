<script>
export default{
    name:"AppHeader",
    props:{
        title:String,
        logo:String,
    },
    data(){

    },
}
</script>


<template>
   <header class="d-flex align-items-center"  >
    <div class="mx-3">
        <img :src="logo" alt="">
    </div>
    <h1>{{ title }}</h1>
   </header>
</template>


<style scoped lang="scss">
header{
    height: 70px;
    img{
        width:70px;
    }
}
</style>