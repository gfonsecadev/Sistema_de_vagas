<template>
  <div>
    <button
      id="botao"
      class="btn btn-primary"
      type="button"
      data-bs-toggle="offcanvas"
      data-bs-target="#offcanvas"
      aria-controls="staticBackdrop"
      @click="getFavoritar"
    >
      Vagas Favoritas
    </button>
    <div
      class="offcanvas offcanvas-end"
      tabindex="-1"
      id="offcanvas"
      aria-labelledby="offcanvasLabel"
    >
      <div class="offcanvas-header">
        <h5 class="offcanvas-title" id="offcanvasLabel">Minhas vagas favoritas</h5>
        <button
          type="button"
          class="btn-close"
          data-bs-dismiss="offcanvas"
          aria-label="Close"
        ></button>
      </div>
      <div class="offcanvas-body">
         <div class="offcanvas-body" v-for="(vaga,cod) in vagasFavoritas" :key="cod">
            <vagas v-bind="vaga" :exibir-botao=false></vagas>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import Vagas from '@/components/comuns/Vagas.vue'

export default {
  name: "VagasFavoritas",

  data:()=>({
    vagasFavoritas:[]
  }),

  mounted() {
     this.emitter.on('favoritar',(e)=>{
            this.vagasFavoritas.push(e)
     })

     this.emitter.on('desfavoritar',(e)=>{
            this.vagasFavoritas.forEach((element,posicao) => {
                if(JSON.stringify(element)==JSON.stringify(e)){
                    this.vagasFavoritas.splice(posicao,1)
                }
            });
     })
  },


  components:{
    Vagas
    
  }
}
</script>

<style scoped>
    #botao{
        position: fixed;
        right: 0;
        z-index: 1;
        
    }
</style>
