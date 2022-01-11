<template>
  <div class="tarefas-grid">
        <template v-if="tarefas.length">
        <Tarefa  v-for="(tarefa,i) in tarefas" 
        :key="tarefa.descricao"
         :tarefa="tarefa"
          @mudarStatus="$emit('mudarStatus', i)"
          @Excluir="$emit('Excluir', i)"/>
        </template>
        <p v-else>Vazio :)</p>
  </div>
</template>

<script>
import Tarefa from './tarefa.vue'
export default {
  components: { Tarefa },

props:{
  tarefas: Array
}

}
</script>

<style>

.tarefas-grid{

  display: flex;
  flex-direction:column-reverse;
  justify-content: center;
  align-items: center;
  width: 90%;
}

</style>