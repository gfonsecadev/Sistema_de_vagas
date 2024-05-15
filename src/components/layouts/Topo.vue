<template>
    <nav class="navbar navbar-expand-sm navbar-dark bg-dark">
        <div class="container">
            <div class="navbar-brand">Vagas</div>
            <button class="navbar-toggler navbar-toggler-icon" data-bs-target="#paginas" data-bs-toggle="collapse" type="button"></button>
            <div id="paginas" class="navbar-collapse collapse">
                <ul class="navbar-nav me-auto">
                    <li class="nav-item"><button @click="acao('Home')" class="nav-link">Home</button></li>
                    <li class="nav-item"><button @click="acao('Vagas')" class="nav-link">Vagas</button></li>
               </ul>
            </div>
            
        </div>
    </nav>
</template>

<script> 

export default{
    name:"Topo",
    methods:{
        acao(p){
            this.$emit('navegar',p)
        }
    }
}

</script>

<style>

</style>