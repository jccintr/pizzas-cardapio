<template>
  
    <div class="toolbar">
            <img class="imgLogo" src="https://raw.githubusercontent.com/jccintr/vue-zqg2rm/master/logopizza-250px.png" alt="">
    </div>
 
</template>

<script>
export default {
  name: 'Cabecalho',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.toolbar {
  
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 80px;
  display: flex;
  align-items: center;
  background-color: #329845;
  justify-content: center;
  font-weight: 600;
}
.titulo {
  font-style: italic;
  margin: 20px;
}
.imgLogo {
  width: 40%;
  
}
</style>
