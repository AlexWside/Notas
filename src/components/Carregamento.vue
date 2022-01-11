<template>
  <div class="carregamento">
     <span class="indicador">{{concluidos}}%</span>
    <div class="carregado" :style="{width: concluidos +'%' }">
      
    </div>
   
  </div>
</template>

<script>
export default {

  props: {
    concluidos: 
    { 
    type: Number,
    default: 0
    }
  }

}
</script>

<style>

.carregamento{
  border: 1px #ccc solid;
  width: 50%;
  height: 2em;
    display: flex;
    flex-direction: column;
  align-items: center;
}
.carregado{
  position: relative;
  height: 100%;
  background-color: #b3ff99;
 align-self: flex-start;
    
}


.indicador{
  position: absolute;
  z-index: 1;

}

</style>