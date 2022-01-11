<template>
  <div class="nova-tarefa">
    <input v-model="descricao" type="text" @keyup.enter="add()">
    <button  @click="add()">+</button>
  </div>
</template>

<script>
export default {

  data(){
    return {
      descricao: ''
    }
  },
  methods: {
    add(){
        this.$emit('adicionar', this.descricao)
        this.descricao = ''
    }
  }

}
</script>

<style>
 .nova-tarefa{
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 2em;
 }

.nova-tarefa input{
  width: 50%;
  height: 2.1em;
  border: #868686 solid 1px;
  background-color: #86868633;
  border-radius: 8px 0 0 8px ;
  outline: none;
  color: #fff;
}


.nova-tarefa button{
    height: 100%;
    color: #fff;
    border: #868686 solid 1px;
    background-color: cornflowerblue;
    border-radius: 0 8px 8px 0;
    width: 50px;
}

</style>