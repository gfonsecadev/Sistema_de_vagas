<template>
    <div v-if="exibir" :class='estilizacao' role="alert">
        <slot :acao='acao'>
            <h4 > Esse é um titulo padrão</h4>
            <p>Essa é uma descrição padrão</p>
        </slot>
       
        <button type="button" class="btn-close" data-bs-dismiss="alert" @click="exibir=false" aria-label="Close"></button>
   </div>
</template>

<script>
   export default{
    name:'Alerta',
    data:()=>({
        exibir:false,
        estilo:'alert-success',
        acao:{}
    }),
    mounted() {
        this.emitter.on('getAlerta',(e)=>{
            this.exibir=e.exibir
            
            switch(e.classe){
                case 'erro':
                     this.estilo='alert-danger'
                     this.acao={titulo:"Opss.Houve um erro!",
                                descricao:"Verifique se você preencheu todos os campos"}
                     break
                case 'sucesso' :
                    this.estilo='alert-success'
                    this.acao={titulo:'Dados salvos',
                               descricao:"Seus dados foram salvo com sucesso"}
                    break
            }

        })
    },

    computed:{
        estilizacao(){
            return `alert ${this.estilo} alert-dismissible fade show`
        }
    }
   }

</script>