<template>

      <div>
            <div class="row mt-4">
                    <pesquisar-vagas></pesquisar-vagas>
            </div>

            <div class="row mt-4" v-for="(vaga,posicao) in vagas" :key="posicao">
                    <div class="col">
                        <vagas v-bind='vaga' :exibir-botao="true"></vagas>
                    </div>     
            </div>
            

            <div class="row mt-4 ">
                <indicador cor-fundo="bg-dark" titulo='Vagas abertas' indicador='224'></indicador>
                <indicador cor-fundo="bg-dark" titulo='Profissionais cadastrados' indicador='189'></indicador>
                <indicador cor-fundo="bg-light" cor-fonte="text-dark" titulo='Usuários logados' :indicador=logados></indicador>
            </div>
      </div>
       
    
</template>

<script>
import PesquisarVagas from "@/components/comuns/PesquisaVaga.vue"
import Indicador from "@/components/comuns/Indicador.vue"
import Vagas from "@/components/comuns/Vagas.vue"


export default{
    name:"Home",
    data:()=>({
        logados:0,
        vagas: []
    }),

    activated() {
        this.vagas=JSON.parse(window.localStorage.getItem("vagas"))

    },

    methods:{
        aleatorio(){
            this.logados=Math.floor(Math.random() *101)+100
        }
        
    },

    mounted() {
        this.emitter.on('buscar',(e)=>{
            this.vagasBusca=JSON.parse(window.localStorage.getItem("vagas"))
            let vagasAux=this.vagasBusca.filter((p)=>p.titulo.toLowerCase().includes(e.toLowerCase()))
            this.vagas=vagasAux
            
        })
    },

    created() {
        setInterval(this.aleatorio,1000)
    },

    components:{
        PesquisarVagas,
        Indicador,
        Vagas
    
    
    }
}

</script>