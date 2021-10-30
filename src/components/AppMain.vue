<template>
    <div class="wrapper">
        <!--<div class="card">
            <h1 class="font-bold text-6xl">Vues With TailwindCSS</h1>
            <h2 class="text-3xl font-bold">Using VueCLI</h2>
        </div>-->
    
        <h1 class="text-3xl block card">{{player}}</h1>
        <h1 class="text-3xl block card">{{playerWinState}}</h1>

<table class="table-fixed m-auto mt-20">
  <tbody>
    <tr>
      <td class="border border-pink-500"><button class="w-16 h-16" id="1" @click="changeText(1)"></button></td>
      <td class="border border-pink-500"><button class="w-16 h-16" id="2" @click="changeText(2)"></button></td>
      <td class="border border-pink-500"><button class="w-16 h-16" id="3" @click="changeText(3)"></button></td>
    </tr>
    <tr>
      <td class="border border-pink-500"><button class="w-16 h-16" id="4" @click="changeText(4)"></button></td>
      <td class="border border-pink-500"><button class="w-16 h-16" id="5" @click="changeText(5)"></button></td>
      <td class="border border-pink-500"><button class="w-16 h-16" id="6" @click="changeText(6)"></button></td>
    </tr>
    <tr>
      <td class="border border-pink-500"><button class="w-16 h-16" id="7" @click="changeText(7)"></button></td>
      <td class="border border-pink-500"><button class="w-16 h-16" id="8" @click="changeText(8)"></button></td>
      <td class="border border-pink-500"><button class="w-16 h-16" id="9" @click="changeText(9)"></button></td>

    </tr>

  </tbody>
</table> 

    </div>
</template>

<script>

    export default {
              
          data() {
          return {
            turn: 0,
            player: "Player-1 (O)",
            playerWinState: "",
            isGameEnded: false
          } 
        },
        methods: {
          changeText(id) {
             if(!this.isGameEnded){
              if(this.turn%2 != 0 ){
                if( document.getElementById(id).innerText == ""){
                  this.turn++;
                  document.getElementById(id).innerText = "X";
                  this.player = "Player-1 (O)";
                }
              }else{
                if( document.getElementById(id).innerText == ""){
                  this.turn++;
                  document.getElementById(id).innerText = "O";
                  this.player = "Player-2 (X)";
                }
              }
             }
           
          },checkForMatches(){
            if((document.getElementById(1).innerText == "X" && document.getElementById(2).innerText == "X" && document.getElementById(3).innerText == "X")||
              (document.getElementById(1).innerText == "O" && document.getElementById(2).innerText == "O" && document.getElementById(3).innerText == "O")){
                document.getElementById(1).style.color = "red";
                document.getElementById(2).style.color = "red";
                document.getElementById(3).style.color = "red";
                document.getElementById(1).style.fontWeight = "bold";
                document.getElementById(2).style.fontWeight = "bold";
                document.getElementById(3).style.fontWeight = "bold";
                this.whoWins();
            }
            else if((document.getElementById(4).innerText == "X" && document.getElementById(5).innerText == "X" && document.getElementById(6).innerText == "X")||
              (document.getElementById(4).innerText == "O" && document.getElementById(5).innerText == "O" && document.getElementById(6).innerText == "O")){
                document.getElementById(4).style.color = "red";
                document.getElementById(5).style.color = "red";
                document.getElementById(6).style.color = "red";
                document.getElementById(4).style.fontWeight = "bold";
                document.getElementById(5).style.fontWeight = "bold";
                document.getElementById(6).style.fontWeight = "bold";
                this.whoWins();
            }
            else if((document.getElementById(7).innerText == "X" && document.getElementById(8).innerText == "X" && document.getElementById(9).innerText == "X")||
              (document.getElementById(7).innerText == "O" && document.getElementById(8).innerText == "O" && document.getElementById(9).innerText == "O")){
                document.getElementById(7).style.color = "red";
                document.getElementById(8).style.color = "red";
                document.getElementById(9).style.color = "red";
                document.getElementById(7).style.fontWeight = "bold";
                document.getElementById(8).style.fontWeight = "bold";
                document.getElementById(9).style.fontWeight = "bold";
                this.whoWins();
            }
            else if((document.getElementById(1).innerText == "X" && document.getElementById(4).innerText == "X" && document.getElementById(7).innerText == "X")||
              (document.getElementById(1).innerText == "O" && document.getElementById(4).innerText == "O" && document.getElementById(7).innerText == "O")){
                document.getElementById(1).style.color = "red";
                document.getElementById(4).style.color = "red";
                document.getElementById(7).style.color = "red";
                document.getElementById(1).style.fontWeight = "bold";
                document.getElementById(4).style.fontWeight = "bold";
                document.getElementById(7).style.fontWeight = "bold";
                this.whoWins();
            }
            else if((document.getElementById(2).innerText == "X" && document.getElementById(5).innerText == "X" && document.getElementById(8).innerText == "X")||
              (document.getElementById(2).innerText == "O" && document.getElementById(5).innerText == "O" && document.getElementById(8).innerText == "O")){
                document.getElementById(2).style.color = "red";
                document.getElementById(5).style.color = "red";
                document.getElementById(8).style.color = "red";
                document.getElementById(2).style.fontWeight = "bold";
                document.getElementById(5).style.fontWeight = "bold";
                document.getElementById(8).style.fontWeight = "bold";
                this.whoWins();
            }
            else if((document.getElementById(3).innerText == "X" && document.getElementById(6).innerText == "X" && document.getElementById(9).innerText == "X")||
              (document.getElementById(3).innerText == "O" && document.getElementById(6).innerText == "O" && document.getElementById(9).innerText == "O")){
                document.getElementById(3).style.color = "red";
                document.getElementById(6).style.color = "red";
                document.getElementById(9).style.color = "red";
                document.getElementById(3).style.fontWeight = "bold";
                document.getElementById(6).style.fontWeight = "bold";
                document.getElementById(9).style.fontWeight = "bold";
                this.whoWins();
            }
            else if((document.getElementById(1).innerText == "X" && document.getElementById(5).innerText == "X" && document.getElementById(9).innerText == "X")||
              (document.getElementById(1).innerText == "O" && document.getElementById(5).innerText == "O" && document.getElementById(9).innerText == "O")){
                document.getElementById(1).style.color = "red";
                document.getElementById(5).style.color = "red";
                document.getElementById(9).style.color = "red";
                document.getElementById(1).style.fontWeight = "bold";
                document.getElementById(5).style.fontWeight = "bold";
                document.getElementById(9).style.fontWeight = "bold";
                this.whoWins();
            }
            else if((document.getElementById(3).innerText == "X" && document.getElementById(5).innerText == "X" && document.getElementById(7).innerText == "X")||
              (document.getElementById(3).innerText == "O" && document.getElementById(5).innerText == "O" && document.getElementById(7).innerText == "O")){
                document.getElementById(3).style.color = "red";
                document.getElementById(5).style.color = "red";
                document.getElementById(7).style.color = "red";
                document.getElementById(3).style.fontWeight = "bold";
                document.getElementById(5).style.fontWeight = "bold";
                document.getElementById(7).style.fontWeight = "bold";
                this.whoWins();
            }  

          },
          whoWins(){
            if(this.turn%2 == 0){
              this.playerWinState = "Player-2 wins";
              this.isGameEnded = true;
              this.player = "";
            }else{
              this.playerWinState = "Player-1 wins";
              this.isGameEnded = true;
              this.player = "";
            }
          }
        },
        updated () {
          this.checkForMatches();
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