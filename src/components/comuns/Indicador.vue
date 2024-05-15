<template>
    
        <div class="col-4">
            <div :class="estilo">
                <h5 class="">{{titulo}}</h5>
                <div class="h-75 d-flex justify-content-center">
                   <h3 class="align-self-center">{{indicador}}</h3>
                </div>
            </div>    
        </div>
  
</template>

<script>
export default{
    name:"Indicador",

     props:['corFundo','corFonte','titulo','indicador'],

    computed:{
        estilo(){
            return ` indicador rounded ${this.corFundo} ${this.corFonte}`
        }
    },
    
   
}

</script>

<style scoped>
    .indicador{
        text-align: center;
        color: white;
        padding: 15px;
        width: 100%;
        height: 200%;
    }
</style>