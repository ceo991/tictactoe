<template>
    <div class="wrapper">
        <!--<div class="card">
            <h1 class="font-bold text-6xl">Vues With TailwindCSS</h1>
            <h2 class="text-3xl font-bold">Using VueCLI</h2>
        </div>-->
    
        <h1 class="text-3xl block card">{{player}}</h1>
   
<table class="table-fixed m-auto mt-20">
  <tbody>
    <tr>
      <td class="border border-pink-500"><button class="p-8" id="1" @click="changeText(1)"></button></td>
      <td class="border border-pink-500"><button class="p-8" id="2" @click="changeText(2)"></button></td>
      <td class="border border-pink-500"><button class="p-8" id="3" @click="changeText(3)"></button></td>
    </tr>
    <tr>
      <td class="border border-pink-500"><button class="p-8" id="4" @click="changeText(4)"></button></td>
      <td class="border border-pink-500"><button class="p-8" id="5" @click="changeText(5)"></button></td>
      <td class="border border-pink-500"><button class="p-8" id="6" @click="changeText(6)"></button></td>
    </tr>
    <tr>
      <td class="border border-pink-500"><button class="p-8" id="7" @click="changeText(7)"></button></td>
      <td class="border border-pink-500"><button class="p-8" id="8" @click="changeText(8)"></button></td>
      <td class="border border-pink-500"><button class="p-8" id="9" @click="changeText(9)"></button></td>

    </tr>s

  </tbody>
</table> 
        
    </div>
</template>

<script>
    export default {
        data() {
          return {
            turn: 0,
            player: "Player-1"
          } 
        },
        methods: {
          changeText(id) {
             this.turn++;
             
              if(this.turn%2 == 0){
                document.getElementById(id).innerText = "X";
                this.player = "Player-1";
              }else{
                document.getElementById(id).innerText = "O";
                this.player = "Player-2";
              }
           
          }
        },
    }
</script>

<style lang="postcss" scoped>
    .wrapper{
        @apply justify-center items-center h-screen text-emerald-500 text-center bg-gray-100 ;
    }
    .card{
        @apply rounded-lg border border-emerald-300 bg-emerald-100 p-10 shadow-lg;
    }

</style>