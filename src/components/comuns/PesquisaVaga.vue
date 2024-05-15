<template>
         
            <div class="col" >
                <div class="card">
                    <h1 class="card-header">Pesquisar Vagas</h1>
                    <div class="card-body form-control">
                        <label>Título da vaga</label>
                        <input class="form-control" type="text" v-model="pesquisa">
                        <small class="text-muted">Informe palavras que estejam relacionadas com o título da vagas que você procura</small>
                        <button class="btn btn-dark form-control" @click="buscarVaga()">Buscar</button>
                    </div>
                </div>
            </div>
       
</template>

<script>
export default{
    name:"PesquisaVaga",
    data:()=>({
        pesquisa:''
    }),
    methods:{
        buscarVaga(){
            this.emitter.emit('buscar',this.pesquisa)
        }
    }

}

</script>