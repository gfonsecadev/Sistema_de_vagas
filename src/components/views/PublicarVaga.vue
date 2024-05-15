<template>
    <div class="border p-4 mt-5 rounded bg-light">
        <div class="row" >
            <div class="col">
                <h4>Apresente a sua vaga para milhares de profissionais e de graça</h4>
                <label>Título da Vaga</label>
                <input type="text" class="form-control" v-model="titulo">
                <div class="form-text">Por exemplo: Programador JavaScript e Vue.JS</div>         
            </div>
        </div>
        <div class="row mt-3">
            <div class="col">
                <label>Descrição</label>
                <textarea class="form-control" v-model="descricao"></textarea>
                <div class="form-text">Informe os detalhes da vaga</div>
            </div>
        </div>
        <div class="row mt-3">
            <div class="col-4">
                <label>Salário</label>
                <input class="form-control" v-model="salario">
            </div>
            <div class="col-4">
                <label>Modalidade</label>
                <select class="form-control" v-model="modalidade">
                    <option value="" disabled>Selecione</option>
                    <option >Home Office</option>
                    <option >Presencial</option>
                </select>
            </div>
            <div class="col-4">
                <label>Tipo</label>
                <select class="form-control" v-model="tipo">
                    <option value="" disabled>Selecione</option>
                    <option >CLT</option>
                    <option >PJ</option>
                </select>
                
            </div>
        </div>
        <div class="row mt-3">
            <div class="col">
                <button class="btn btn-dark form-control" @click="salvarVagas()">Salvar</button>
            </div>
        </div>

    </div>
</template>

<script>
export default{
    name:"Vagas",
    data:()=>({
        titulo:'',
        descricao:'',
        salario:'',
        modalidade:'',
        tipo:'',
        publicacao:''
    }),

    methods:{
        salvarVagas(){
            let vagas=JSON.parse(window.localStorage.getItem('vagas'))
            if(vagas==null) vagas=[]
            let horaAtual=Date.now()
            this.publicacao=new Date(horaAtual).toLocaleString('pt-br')
            
            vagas.push({
                titulo: this.titulo,
                descricao: this.descricao,
                salario:this.salario,
                modalidade:this.modalidade,
                tipo:this.tipo,
                publicacao:this.publicacao
             
            })
        if(this.titulo!=='' && this.descricao!=='' && this.salario!=='' && this.modalidade!=='' && this.tipo!==''){
              this.emitter.emit('getAlerta',{
                    exibir: true,
                    classe:'sucesso'
                })
                window.localStorage.setItem('vagas',JSON.stringify(vagas))
                this.limparCampos()
            }else{
                this.emitter.emit('getAlerta',{
                    exibir: true,
                    classe:'erro'
                })
                
            }

           
       },

       limparCampos(){
            this.titulo="",
            this.descricao="",
            this.salario="",
            this.modalidade="",
            this.tipo=""
       }
    }
}

</script>