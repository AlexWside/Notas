<template>
  <div class="main">
    <Carregamento :concluidos="progresso"/>
    <h1>Notas</h1>
    <NovaTarefa @adicionar="adicionar" />
    <TarefasGrid
      :tarefas="tarefas"
      @mudarStatus="mudarStatus"
      @Excluir="excluir"
    />
  </div>
</template>

<script>
import Carregamento from './components/Carregamento.vue';
import NovaTarefa from './components/novaTarefa.vue';
import TarefasGrid from './components/tarefasGrid.vue';
export default {
  created() {
     const array =   JSON.parse(localStorage.getItem('tarefas')) 
    if(Array.isArray(array))
      this.tarefas = array

  },
  components: { TarefasGrid, NovaTarefa, Carregamento },
 data(){
   return  {
     tarefas : []
   }
 }, methods: {
    mudarStatus(i){
     this.tarefas[i].status = !this.tarefas[i].status
    },
    excluir(i){
        this.tarefas.splice(i, 1);
    },
    adicionar(t){
      const sameDescription  = valor => valor.descricao === t
      
      const valido  = this.tarefas.filter(sameDescription).length == 0

      if(valido && t != ""){
          this.tarefas.push({
            descricao: t,
            status: false
          })
      }
      
      }
 },
 watch: {
   tarefas: {
    deep: true,
    handler(){ 
      localStorage.setItem('tarefas', JSON.stringify(this.tarefas) )
      }
 }

},
computed: {
    progresso(){
      const total = this.tarefas.length
      const concluido =  this.tarefas.filter(valor => valor.status).length

      return Math.round((concluido/total) * 100)
    }
}

}

</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins&display=swap");

body {
  background-color: #8ec5fc;
  background-image: linear-gradient(62deg, #8ec5fc 0%, #e0c3fc 100%);
  font-family: "Poppins", sans-serif;
}

.main {
  margin-top: 10%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.main h1 {
  color: #fff;
}

.main NovaTarefa {
  margin-bottom: 5%;
}
</style>
