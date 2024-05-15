<template>
    <div class="container ">
    <keep-alive>    
     <component :is="pagina"/>
    </keep-alive>
    </div>
</template>

<script> 
import Home from "@/components/views/Home.vue"
import Vagas from "@/components/views/PublicarVaga.vue"
export default{
    props:{
        pagina:String
    },
    name:"Container",

    components:{
        Home,
        Vagas
    }
}

</script>

<style>

</style>