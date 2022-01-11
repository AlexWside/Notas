<template>
  <div class="tarefa" :class="estiloClass" @click="$emit('mudarStatus', tarefa)">
    <button class="close" @click="$emit('Excluir', tarefa)">x</button>
    <p>{{ tarefa.descricao }}</p>
  </div>
</template>

<script>
export default {
  props: {
    tarefa: Object,
  },
  computed: {
    estiloClass() {
      return {
        concluido: this.tarefa.status,

        pendente: !this.tarefa.status,
      };
    },
  },
};
</script>

<style>
.tarefa {
  position: relative;
  box-sizing: border-box;
  padding: 10px;
  margin: 1em;
  width: 80%;
  border-radius: 10px;
  color: #fff;
  text-align: center;  
  font-weight: 800;
  
}

.close{
  position: absolute;
  right: 10px;
  top: 10px;
  border: none;
  border-radius: 50%;
  color:#fff;
  font-weight: 600;
}

.concluido {
  background-color: #6f8ada;
  color: #ccc;
     text-decoration: line-through;
}

.concluido  .close {
  background-color: #385bc2;
}

.pendente {
  background-color: #ffff80;
  color: black;
}

.pendente .close{
  background-color: #e6e600;
}
</style>