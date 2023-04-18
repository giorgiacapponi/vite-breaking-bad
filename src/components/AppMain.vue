<script>
import AppHeader from './AppHeader.vue';
import AppCard from './AppCard.vue';
import { store } from "../store";
import AppSelect from "./AppSelect.vue";
import axios from "axios";
export default {
    name: "AppMain",
    components: { AppHeader, AppCard, AppSelect },
    data() {
        return {
            store,
            optValue: "all"
        }

    },
    methods: {
        filterType() {
            if (this.optValue == "Alien") {
                axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0&archetype=Alien")
                    .then((resp) => {
                        this.store.cards= resp.data.data;
                        this.store.numberCards=this.store.cards.length
                        console.log(this.store.numberCards);
                    })
            }else if ( this.optValue== "Ally of Justice"){
                axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=Melodious")
                .then((resp)=>{
                    this.store.cards= resp.data.data;
                    this.store.numberCards=this.store.cards.length
                    console.log(myData);
                })
            }else if ( this.optValue== "Ancient Gear"){
                axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=Blue-Eyes")
                .then((resp)=>{
                    this.store.cards= resp.data.data;
                    this.store.numberCards=this.store.cards.length
                    console.log(this.store.cards.length);
                })
            }else{
                axios
  .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
  .then((resp) => {
      this.store.cards = resp.data.data;
      this.store.numberCards=this.store.cards.length
      console.log(this.store.cards);
    })
            }
        }
    }


}
</script>


<template>
    <main class="py-5">

        <select name="" id="type" v-model="optValue" @change="filterType()">
            <AppSelect />
        </select>
        <div class="container bg-light py-5">
            <div class="container py-3">
                <AppHeader class="header-main " :title="`found ${store.numberCards}`" />
                <div class="container-card">
                    <div class="row row-cols-5 g-5 ">
                        <div class="col" v-for="(card, index) in store.cards" key="card.id">
                            <AppCard :title="card.name" :type="card.archetype"
                                :imgUrl="card.card_images[0].image_url_cropped" />

                        </div>

                    </div>
                </div>
            </div>
        </div>

    </main>
</template>


<style scoped lang="scss">
@use "../styles/variables.scss" as *;

main {
    background-color: $bgColorMain ;

    select {
        width: 70px;
        height: 40px;
        margin-left: 7rem;
        margin-bottom: 3rem;
    }

    .header-main {
        background-color: black;
        color: white;

    }

}</style>