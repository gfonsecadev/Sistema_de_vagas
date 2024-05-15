<template>
    
        <div class="col">
            <div class="card">
                <div class="card-header d-flex justify-content-between">
                    <h1 >{{titulo}}</h1>
                    <div v-if="exibirBotao" class="form-check form-switch">
                        <input type="checkbox" class="form-check-input" v-model="favoritar">
                        <label class="form-check-label">Favoritar</label>
                   
                    </div>
                </div>
                <div class="card-body">
                    <p>{{descricao}}</p>
                </div>
                <div class="card-footer">
                    <small class="text muted">Salário R$ {{salario}} | Modalidade: {{modalidade}} | Tipo: {{tipo}} | Publicação: {{publicacao}}</small>
                </div>
            </div>
        </div>
    
</template>


<script>

export default ({
    name:"vagas",

    data:()=>({
        favoritar:'false'
    }),

    props:{
        exibirBotao:{
            type:Boolean,
            default:false
        },
        salario: String,
        modalidade:String,
        descricao:{
            type:String,
            default(){
                return "Não foi inserido nenhuma descrição sobre essa vaga"}
        },
        titulo:String,
        tipo:String,
        publicacao:String
    },

    watch:{
        favoritar(novo){
            let vaga={
                    salario:this.salario,
                    titulo:this.titulo,
                    modalidade:this.modalidade,
                    tipo:this.tipo,
                    descricao:this.descricao,
                    publicacao:this.publicacao
            }
            if(novo){
                 
                this.emitter.emit('favoritar',vaga)
            }else{
                this.emitter.emit('desfavoritar',vaga)
            }
           
        }
    }
})
</script>
