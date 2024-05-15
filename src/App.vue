<template>
<div id="App">
  <topo @navegar='componente=$event'></topo>
  <alerta >
      <template v-slot:default='slotProps'> 
          <h4>{{slotProps.acao.titulo}}</h4>
          <p>{{slotProps.acao.descricao}}</p> 
      </template>

      
  </alerta>
  <vagas-favoritas></vagas-favoritas>
  <conteudo :pagina='componente'></conteudo>
  
  
</div>
</template>

<script>
import Topo from './components/layouts/Topo.vue'
import Conteudo from './components/layouts/Conteudo.vue'
import VagasFavoritas from '@/components/layouts/VagasFavoritas.vue'
import Alerta from '@/components/comuns/Alerta.vue'

export default {
  name: 'App',
  data() {
    return {
      componente:'Home',
      exibicao:''
      
    }
  },
  components: {
    Topo,
    Conteudo,
    VagasFavoritas,
    Alerta,

  }
}
</script>

<style >
 #App{
  position: relative;
 }
</style>
