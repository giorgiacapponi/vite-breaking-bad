<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from "./components/AppMain.vue";
import {store} from "./store";
import axios from "axios";
export default{
    components: { AppHeader,AppMain },
    data(){
        return{
            store
        }
    },
    mounted(){
        axios
  .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
  .then((resp) => {
      this.store.cards = resp.data.data;
      console.log(this.store.cards);
    })

    }
}
</script>

<template>

<AppHeader class="header" title="Yu-Gi-Oh API" logo="https://img.tuttoandroid.net/wp-content/uploads/2016/01/Yu-Gi-Oh-Gioco-Android-Konami-e1452552439561.jpg"/>
<AppMain/>
</template>


<style lang="scss">
@use "./styles/general.scss";


</style>