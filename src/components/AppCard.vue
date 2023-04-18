<script>

export default{
    name:"AppCard",
    props:{
      imgUrl:String,
      title:String,
      type:String,
    },
    data(){
      
    },
}
</script>

<template>
   <div class="card" >
  <img class="card-img-top" :src="imgUrl" alt="Card image cap">
  <div class="card-body">
    <h5 class="card-title">{{ title }}</h5>
    <p class="card-text">{{ type }}</p>
  
  </div>
</div>


</template>


<style scoped lang="scss" > 
@use "../styles/variables.scss";

.card{
  height: 100%;
background-color:#d48f38}

</style>