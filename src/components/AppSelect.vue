<script>
export default{
    name:"AppSelect",
    data(){
        return{
            selectOption:["all", "Alien", "Ally of Justice","Ancient Gear"],
            
        }
    }
}
</script>


<template>
    <option :value="opt" v-for="opt in selectOption"  >
        {{ opt }}
    </option>
</template>