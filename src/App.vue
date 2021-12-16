<template>
<div class="wrapper">
  <fiftin-puzzle></fiftin-puzzle>
</div>
</template>

<script>
import FiftinPuzzle from './components/FiftinPuzzle.vue'
export default {
  name: 'App',
 data(){

 } ,
 components:{
   FiftinPuzzle,
 }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
}
.wrapper{
height: 100vh;
display: flex;
justify-content: center;
align-items: center;
position: relative;
    perspective: 800px;
    perspective-origin: 50%;
}
</style>
