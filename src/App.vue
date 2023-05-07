<template>
  <div class="wrapper">
    <h2 class="header">fifteen Puzzle</h2>
    <transition name="win">
      <div v-if="victory" class="win">
        <div class="title">Congratulations! You win🎉</div>
        <div @click="reload" class="reload">Try again <i class="fas fa-redo"></i></div>
      </div>
    </transition>
    <fiftin-puzzle @victory="win"></fiftin-puzzle>
    <div class="construction"><i class="fas fa-info-circle"></i> Use arrow keys(← →,↓ ↑) to move blocks</div>
  </div>
</template>

<script>
import FiftinPuzzle from './components/FiftinPuzzle.vue'
export default {
  name: 'App',
 data(){
   return{
     victory : false,
   }
 } ,
 components:{
   FiftinPuzzle,
 },
 methods:{
   win(e){
     this.victory = e
   },
   reload(){
     window.location.reload();
   }
 }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}
.wrapper {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
  perspective: 800px;
  perspective-origin: center;
  .header{
    font-size: 35px;
    text-transform: uppercase;
  }
  .win {
    position: absolute;
    top: 240px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 20px;
    color: white;
    border-radius: 5px;
    z-index: 5;
    background: linear-gradient(to right, #67052b, #32675b);
    .title {
      font-size: 280%;
      margin-bottom: 5px;
      white-space: nowrap;
    }
    .reload{
      color: black;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 20px;
      padding: 5px 10px;
      border: 1px solid red;
      border-radius: 5px;
      transition: all .5s ease;
      cursor: pointer;
      i{
        margin-left: 5px;
      }
      &:hover{
        transform: scale(1.2);
        background: linear-gradient(to right, #b7094c, #61c2ad);
        color: white;
        i{
          transition: all .5s ease;
          transform: scale(1.3) rotate(360deg);
        }
      }
    }
  }
  .construction {
    font-size: 30px;
    margin-top: 40px;
  }
}
.win-enter-from {
  transform: translateY(-300px) rotate(-180deg);
}
.win-enter-active {
  transition: all 1s ease-in-out;
}
.win-enter-to {
  transform: translateY(0px) rotate(0deg);
}
</style>
