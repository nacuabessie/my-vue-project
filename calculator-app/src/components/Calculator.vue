<template>
    <div class="mt-[9rem] ml-[30rem] h-60 w-[23rem] ">
      <div class="bg-amber-600 text-center pt-5 pb-5 text-4xl rounded-t-xl">{{current || '0'}}</div>
      <div class="grid grid-cols-2 gap-9 pt-4 pb-4 bg-stone-600 text-white">
        <div @click="clear" class="text-xl w-[15rem] text-center">C</div> 
        <div @click="divide" class=" text-[#CC7351] font-bold text-2xl pl-[7rem]">÷</div>
      </div>
      <div class="grid grid-rows-3 grid-cols-4 gap-9 p-5  leading-normal bg-stone-800 text-white text-center">
        <div @click="append('7')" class="text-xl">7</div>
        <div @click="append('8')" class="text-xl">8</div>
        <div @click="append('9')" class="text-xl">9</div>  
        <div @click="times" class="text-[#CC7351] font-bold text-2xl">x</div>  
        <div @click="append('4')" class="text-xl">4</div>
        <div @click="append('5')" class="text-xl">5</div>
        <div @click="append('6')" class="text-xl">6</div>
        <div @click="minus" class="text-[#CC7351] font-bold text-2xl">-</div>
        <div @click="append('1')" class="text-xl">1</div>
        <div @click="append('2')" class="text-xl">2</div>
        <div @click="append('3')" class="text-xl">3</div>
        <div @click="add" class="text-[#CC7351] font-bold text-2xl">+</div>
      </div>
      <div class="grid grid-cols-3 gap-9 pt-4 pb-4 bg-stone-600 text-white text-center rounded-b-xl">
        <div @click="append('0')" class="text-xl">0</div>
        <div @click="dot" class="text-xl">.</div>
        <div @click="equal" class="text-[#CC7351] text-2xl">=</div>
      </div>
      
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        previous: null,
        current: '',
        operator: null,
        operatorClicked: false,
      }
    },
    methods: {
      clear() {
        this.current = '';
      },
      append(number) {
        if (this.operatorClicked) {
          this.current = '';
          this.operatorClicked = false;
        }
        this.current = `${this.current}${number}`;
      },
      dot() {
        if (this.current.indexOf('.') === -1) {
          this.append('.');
        }
      },

      setPrevious() {
        this.previous = this.current;
        this.operatorClicked = true;
      },
      divide() {
        this.operator = (a, b) => a / b;
        this.setPrevious();
      },
      times() {
        this.operator = (a, b) => a * b;
        this.setPrevious();
      },
      minus() {
        this.operator = (a, b) => a - b;
        this.setPrevious();
      },
      add() {
        this.operator = (a, b) => a + b;
        this.setPrevious();
      },
      equal() {
        this.current = `${this.operator(
          parseFloat(this.current), 
          parseFloat(this.previous)
        )}`;
        this.previous = null;
      }
    }
  }
  </script>
  
  <style scoped>
  /* .calculator {
    margin: 0 auto;
    width: 400px;
    font-size: 40px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
  }
  .display {
    grid-column: 1 / 5;
    background-color: #333;
    color: white;
  }
  .zero {
    grid-column: 1 / 3;
  }
  .text-xl {
    background-color: #F2F2F2;
    border: 1px solid #999;
  }
  .operator {
    background-color: orange;
    color: white;
  } */
  </style>








<!-- <script>
export default{
    data(){
        return{
            current:'',
        }
    },

    methods:{
        add(){
        },
        subtract(){

        },

        append(number){
            this.current = "${this.current}${number}";
        }
    }
}
</script>

<template>
<div class="h-60 w-[16rem]">
<div class="bg-amber-600 text-center">{{ current || 0 }}</div>
<div class="grid  grid-rows-5 grid-cols-4 gap-9 pt-5 leading-normal bg-stone-600 text-white text-center">
    <div @click="append('1')">1</div>
    <div @click="append('2')">2</div>
    <div @click="append('3')">3</div>
    <div @click="add">+</div>
    <div @click="append('4')">4</div>
    <div @click="append('5')">5</div>
    <div @click="append('6')">6</div>
    <div @click="subtract">-</div>
    <div @click="append('7')">7</div>
    <div @click="append('8')">8</div>
    <div @click="append('9')">9</div>
    <div @click="multiply">x</div>
    <div @click="append('0')">0</div>
    <div>.</div>
    <div>=</div>
    <div @click="divide">/</div>
</div>
<div class="grid">
</div>
</div>
</template> -->