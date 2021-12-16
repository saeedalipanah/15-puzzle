<template>
  <div class="puzzle-wrapper">
    <div class="items" v-for="(item, index) in items" :key="index">
      <div class="item" :class="item==-1 ? 'empty-block': ''">{{ item }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15,-1],
    };
  },
  mounted() {
    window.addEventListener("keydown", this.movement);
    this.shuffle(this.items,15);
   
  },
  created(){
  },
  methods: {
    movement(e) {
      let emptyBlock = this.items.indexOf(-1);
      if (e.code === "ArrowUp") {
        if (
          emptyBlock == "12" ||
          emptyBlock == "13" ||
          emptyBlock == "14" ||
          emptyBlock == "15"
        )
          return;
        else {
          let v = this.items[emptyBlock];
          this.items[emptyBlock] = this.items[emptyBlock + 4];
          this.items[emptyBlock + 4] = v;
        }
      } else if (e.code === "ArrowDown") {
        if (
          emptyBlock == "0" ||
          emptyBlock == "1" ||
          emptyBlock == "2" ||
          emptyBlock == "3"
        ) {
          return;
        } else {
          let v = this.items[emptyBlock];
          this.items[emptyBlock] = this.items[emptyBlock - 4];
          this.items[emptyBlock - 4] = v;
        }
      } else if (e.code === "ArrowRight") {
        if (
          emptyBlock == "0" ||
          emptyBlock == "4" ||
          emptyBlock == "8" ||
          emptyBlock == "12"
        ) {
          return;
        } else {
          let v = this.items[emptyBlock];
          this.items[emptyBlock] = this.items[emptyBlock - 1];
          this.items[emptyBlock - 1] = v;
        }
      } else if (e.code === "ArrowLeft")
        if (
          emptyBlock == "3" ||
          emptyBlock == "7" ||
          emptyBlock == "11" ||
          emptyBlock == "15"
        )
          return;
        else {
          let v = this.items[emptyBlock];
          this.items[emptyBlock] = this.items[emptyBlock + 1];
          this.items[emptyBlock + 1] = v;
        }
    },
     shuffle(array, len = array.length) {
        for (let i = array.length - 1; i > 0; i--) {
            let j = Math.floor(Math.random() * (i + 1));
            [array[i], array[j]] = [array[j], array[i]];
        }
        return array.slice(0, len);
    },
  },
};
</script>

<style lang="scss" scoped>
.puzzle-wrapper {
  padding: 0.8rem;
  width: 32rem;
  height: 32rem;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 1fr);
  grid-gap: 0.8rem;
  background-color: gray;
  border-radius: 1rem;
  transform: rotateX(60deg);
  box-shadow: rgba(0, 0, 0, 0.8) 0px 40px 10px, rgba(0, 0, 0, 0.7) 0px 15px 12px;
  
    .item {
      position: relative;
      font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
      display: flex;
      justify-content: center;
      align-items: center;
      grid-column: 1;
      grid-row: 1;
      font-size: 2.2rem;
      width: 100%;
      height: 100%;
      color :white;
      background-color: black;
      perspective: 100px;
      &.empty-block{
        background-color: red;
        color: transparent;
        display: none;
      }
    }
  
}
</style>
