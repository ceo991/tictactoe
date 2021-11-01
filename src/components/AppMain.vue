<template>
  <div class="wrapper">
    <h1 class="text-3xl block card italic">{{ player }}</h1>
    <h1 class="text-3xl block card italic">{{ playerWinState }}</h1>
    <div class="score-card">
      <span class="italic"><strong>Player-1:</strong> {{ p1score }}</span>
      <span class="italic"><strong>Player-2:</strong> {{ p2score }}</span>
    </div>
    <table class="table-fixed m-auto mt-10" cellpadding="0" cellspacing="0">
      <tbody>
        <tr>
          <td class="border border-pink-500" style="height: 80px; width: 80px">
            <div style="height: 100%; width: 100%;">
              <button  id="1" @click="changeText(1)" style="height: 100%; width: 100%;"></button>
            </div>
          </td>
          <td class="border border-pink-500" style="height: 80px; width: 80px">
            <div style="height: 100%; width: 100%;">
              <button  id="2" @click="changeText(2)" style="height: 100%; width: 100%;"></button>
            </div>
          </td>
          <td class="border border-pink-500" style="height: 80px; width: 80px">
            <div style="height: 100%; width: 100%;">
              <button  id="3" @click="changeText(3)" style="height: 100%; width: 100%;"></button>
            </div>
          </td>
        </tr>
        <tr style="height: 80px">
          <td class="border border-pink-500" style="height: 80px; width: 80px">
            <div style="height: 100%; width: 100%;">
              <button  id="4" @click="changeText(4)" style="height: 100%; width: 100%;"></button>
            </div>
          </td>
          <td class="border border-pink-500" style="height: 80px; width: 80px">
            <div style="height: 100%; width: 100%;">
              <button  id="5" @click="changeText(5)" style="height: 100%; width: 100%;"></button>
            </div>
          </td>
          <td class="border border-pink-500" style="height: 80px; width: 80px">
            <div style="height: 100%; width: 100%;">
              <button  id="6" @click="changeText(6)" style="height: 100%; width: 100%;"></button>
            </div>
          </td>
        </tr>
        <tr style="height: 80px">
          <td class="border border-pink-500" style="height: 80px; width: 80px">
            <div style="height: 100%; width: 100%;">
              <button  id="7" @click="changeText(7)" style="height: 100%; width: 100%;"></button>
            </div>
          </td>
          <td class="border border-pink-500" style="height: 80px; width: 80px">
            <div style="height: 100%; width: 100%;">
              <button  id="8" @click="changeText(8)" style="height: 100%; width: 100%;"></button>
            </div>
          </td>
          <td class="border border-pink-500" style="height: 80px; width: 80px">
            <div style="height: 100%; width: 100%;">
              <button  id="9" @click="changeText(9)" style="height: 100%; width: 100%;"></button>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
    <button class="button mt-8" @click="resetGame()">Reset</button>

    <transition name="fade" appear>
      <div
        class="modal-overlay"
        v-if="isGameEnded"
        @click="showModal = false"
      ></div>
    </transition>
    <transition name="slide" appear>
      <div class="modal" v-if="isGameEnded">
        <h1><strong> GAME OVER ! </strong></h1>
        <p class="mt-3 italic">{{ playerWinState }}</p>
        <button class="button mt-5" @click="playAgain()">Play Again</button>
      </div>
    </transition>

    <transition name="fade">
      <div
        class="
          card
          w-full
          h-screen
          fixed
          top-0
          bottom-0
          right-0
          left-0
          text
          justify-items-center
          items-center
          flex-col
        "
        v-if="playButtonPressed"
      >
        <h1
          class="
            text-2xl
            title-card
            h-48
            w-80
            flex
            justify-items-center
            items-center
          "
        >
          <strong><em>TİC-TAC-TOE</em></strong>
        </h1>
        <button class="button w-60 mt-7" @click="playButtonPressed = false">
          PLAY ! ! !
        </button>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      turn: 0,
      player: "Player-1 (O)",
      playerWinState: "",
      isGameEnded: false,
      p1score: 0,
      p2score: 0,
      playButtonPressed: true,
    };
  },
  methods: {
    changeText(id) {
      if (!this.isGameEnded) {
        if (this.turn % 2 != 0) {
          if (document.getElementById(id).innerText == "") {
            this.turn++;
            document.getElementById(id).innerText = "X";
            this.player = "Player-1 (O)";
          }
        } else {
          if (document.getElementById(id).innerText == "") {
            this.turn++;
            document.getElementById(id).innerText = "O";
            this.player = "Player-2 (X)";
          }
        }
      }
    },
    checkForMatches() {
      if (
        (document.getElementById(1).innerText == "X" &&
          document.getElementById(2).innerText == "X" &&
          document.getElementById(3).innerText == "X") ||
        (document.getElementById(1).innerText == "O" &&
          document.getElementById(2).innerText == "O" &&
          document.getElementById(3).innerText == "O")
      ) {
        document.getElementById(1).style.color = "red";
        document.getElementById(2).style.color = "red";
        document.getElementById(3).style.color = "red";
        document.getElementById(1).style.fontWeight = "bold";
        document.getElementById(2).style.fontWeight = "bold";
        document.getElementById(3).style.fontWeight = "bold";
        this.whoWins();
      } else if (
        (document.getElementById(4).innerText == "X" &&
          document.getElementById(5).innerText == "X" &&
          document.getElementById(6).innerText == "X") ||
        (document.getElementById(4).innerText == "O" &&
          document.getElementById(5).innerText == "O" &&
          document.getElementById(6).innerText == "O")
      ) {
        document.getElementById(4).style.color = "red";
        document.getElementById(5).style.color = "red";
        document.getElementById(6).style.color = "red";
        document.getElementById(4).style.fontWeight = "bold";
        document.getElementById(5).style.fontWeight = "bold";
        document.getElementById(6).style.fontWeight = "bold";
        this.whoWins();
      } else if (
        (document.getElementById(7).innerText == "X" &&
          document.getElementById(8).innerText == "X" &&
          document.getElementById(9).innerText == "X") ||
        (document.getElementById(7).innerText == "O" &&
          document.getElementById(8).innerText == "O" &&
          document.getElementById(9).innerText == "O")
      ) {
        document.getElementById(7).style.color = "red";
        document.getElementById(8).style.color = "red";
        document.getElementById(9).style.color = "red";
        document.getElementById(7).style.fontWeight = "bold";
        document.getElementById(8).style.fontWeight = "bold";
        document.getElementById(9).style.fontWeight = "bold";
        this.whoWins();
      } else if (
        (document.getElementById(1).innerText == "X" &&
          document.getElementById(4).innerText == "X" &&
          document.getElementById(7).innerText == "X") ||
        (document.getElementById(1).innerText == "O" &&
          document.getElementById(4).innerText == "O" &&
          document.getElementById(7).innerText == "O")
      ) {
        document.getElementById(1).style.color = "red";
        document.getElementById(4).style.color = "red";
        document.getElementById(7).style.color = "red";
        document.getElementById(1).style.fontWeight = "bold";
        document.getElementById(4).style.fontWeight = "bold";
        document.getElementById(7).style.fontWeight = "bold";
        this.whoWins();
      } else if (
        (document.getElementById(2).innerText == "X" &&
          document.getElementById(5).innerText == "X" &&
          document.getElementById(8).innerText == "X") ||
        (document.getElementById(2).innerText == "O" &&
          document.getElementById(5).innerText == "O" &&
          document.getElementById(8).innerText == "O")
      ) {
        document.getElementById(2).style.color = "red";
        document.getElementById(5).style.color = "red";
        document.getElementById(8).style.color = "red";
        document.getElementById(2).style.fontWeight = "bold";
        document.getElementById(5).style.fontWeight = "bold";
        document.getElementById(8).style.fontWeight = "bold";
        this.whoWins();
      } else if (
        (document.getElementById(3).innerText == "X" &&
          document.getElementById(6).innerText == "X" &&
          document.getElementById(9).innerText == "X") ||
        (document.getElementById(3).innerText == "O" &&
          document.getElementById(6).innerText == "O" &&
          document.getElementById(9).innerText == "O")
      ) {
        document.getElementById(3).style.color = "red";
        document.getElementById(6).style.color = "red";
        document.getElementById(9).style.color = "red";
        document.getElementById(3).style.fontWeight = "bold";
        document.getElementById(6).style.fontWeight = "bold";
        document.getElementById(9).style.fontWeight = "bold";
        this.whoWins();
      } else if (
        (document.getElementById(1).innerText == "X" &&
          document.getElementById(5).innerText == "X" &&
          document.getElementById(9).innerText == "X") ||
        (document.getElementById(1).innerText == "O" &&
          document.getElementById(5).innerText == "O" &&
          document.getElementById(9).innerText == "O")
      ) {
        document.getElementById(1).style.color = "red";
        document.getElementById(5).style.color = "red";
        document.getElementById(9).style.color = "red";
        document.getElementById(1).style.fontWeight = "bold";
        document.getElementById(5).style.fontWeight = "bold";
        document.getElementById(9).style.fontWeight = "bold";
        this.whoWins();
      } else if (
        (document.getElementById(3).innerText == "X" &&
          document.getElementById(5).innerText == "X" &&
          document.getElementById(7).innerText == "X") ||
        (document.getElementById(3).innerText == "O" &&
          document.getElementById(5).innerText == "O" &&
          document.getElementById(7).innerText == "O")
      ) {
        document.getElementById(3).style.color = "red";
        document.getElementById(5).style.color = "red";
        document.getElementById(7).style.color = "red";
        document.getElementById(3).style.fontWeight = "bold";
        document.getElementById(5).style.fontWeight = "bold";
        document.getElementById(7).style.fontWeight = "bold";
        this.whoWins();
      } else if (
        document.getElementById(1).innerText != "" &&
        document.getElementById(2).innerText != "" &&
        document.getElementById(3).innerText != "" &&
        document.getElementById(4).innerText != "" &&
        document.getElementById(5).innerText != "" &&
        document.getElementById(6).innerText != "" &&
        document.getElementById(7).innerText != "" &&
        document.getElementById(8).innerText != "" &&
        document.getElementById(9).innerText != ""
      ) {
        this.playerWinState = "It's a draw !";
        this.isGameEnded = true;
        this.player = "";
      }
    },
    whoWins() {
      if (!this.isGameEnded) {
        if (this.turn % 2 == 0) {
          this.playerWinState = "Player-2 wins";
          this.p2score++;
          this.isGameEnded = true;
          this.player = "";
        } else {
          this.playerWinState = "Player-1 wins";
          this.p1score++;
          this.isGameEnded = true;
          this.player = "";
        }
      }
    },
    playAgain() {
      this.isGameEnded = false;
      this.playerWinState = "";
      this.turn = 0;
      this.player = "Player-1 (O)";
      document.getElementById(1).innerText = "";
      document.getElementById(2).innerText = "";
      document.getElementById(3).innerText = "";
      document.getElementById(4).innerText = "";
      document.getElementById(5).innerText = "";
      document.getElementById(6).innerText = "";
      document.getElementById(7).innerText = "";
      document.getElementById(8).innerText = "";
      document.getElementById(9).innerText = "";

      document.getElementById(1).style.color = "inherit";
      document.getElementById(2).style.color = "inherit";
      document.getElementById(3).style.color = "inherit";
      document.getElementById(1).style.fontWeight = "normal";
      document.getElementById(2).style.fontWeight = "normal";
      document.getElementById(3).style.fontWeight = "normal";
      document.getElementById(4).style.color = "inherit";
      document.getElementById(5).style.color = "inherit";
      document.getElementById(6).style.color = "inherit";
      document.getElementById(4).style.fontWeight = "normal";
      document.getElementById(5).style.fontWeight = "normal";
      document.getElementById(6).style.fontWeight = "normal";
      document.getElementById(7).style.color = "inherit";
      document.getElementById(8).style.color = "inherit";
      document.getElementById(9).style.color = "inherit";
      document.getElementById(7).style.fontWeight = "normal";
      document.getElementById(8).style.fontWeight = "normal";
      document.getElementById(9).style.fontWeight = "normal";
    },
    resetGame() {
      this.isGameEnded = false;
      this.playerWinState = "";
      this.turn = 0;
      this.player = "Player-1 (O)";
      this.p1score = 0;
      this.p2score = 0;
      document.getElementById(1).innerText = "";
      document.getElementById(2).innerText = "";
      document.getElementById(3).innerText = "";
      document.getElementById(4).innerText = "";
      document.getElementById(5).innerText = "";
      document.getElementById(6).innerText = "";
      document.getElementById(7).innerText = "";
      document.getElementById(8).innerText = "";
      document.getElementById(9).innerText = "";

      document.getElementById(1).style.color = "inherit";
      document.getElementById(2).style.color = "inherit";
      document.getElementById(3).style.color = "inherit";
      document.getElementById(1).style.fontWeight = "normal";
      document.getElementById(2).style.fontWeight = "normal";
      document.getElementById(3).style.fontWeight = "normal";
      document.getElementById(4).style.color = "inherit";
      document.getElementById(5).style.color = "inherit";
      document.getElementById(6).style.color = "inherit";
      document.getElementById(4).style.fontWeight = "normal";
      document.getElementById(5).style.fontWeight = "normal";
      document.getElementById(6).style.fontWeight = "normal";
      document.getElementById(7).style.color = "inherit";
      document.getElementById(8).style.color = "inherit";
      document.getElementById(9).style.color = "inherit";
      document.getElementById(7).style.fontWeight = "normal";
      document.getElementById(8).style.fontWeight = "normal";
      document.getElementById(9).style.fontWeight = "normal";
    },
  },
  updated() {
    this.checkForMatches();
  },
};
</script>

<style lang="postcss" scoped>
.wrapper {
  @apply justify-center items-center h-screen text-emerald-500 text-center bg-gray-100;
}
.card {
  @apply flex justify-center rounded-lg border border-emerald-300 bg-emerald-100 p-10 shadow-lg;
}

.title-card {
  @apply flex justify-center rounded-lg border border-pink-500 bg-emerald-100 p-10 shadow-lg;
}

.score-card {
  @apply flex justify-around rounded-lg border text-emerald-900 border-emerald-300 bg-emerald-100 p-10 shadow-lg;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "montserrat", sans-serif;
}

#app {
  position: relative;

  display: flex;
  justify-content: center;
  align-items: center;

  width: 100vw;
  min-height: 100vh;
  overflow-x: hidden;
}

.button {
  appearance: none;
  outline: none;
  border: none;
  background: none;
  cursor: pointer;

  display: inline-block;
  padding: 15px 25px;
  background-image: linear-gradient(to right, #cc2e5d, #ff5858);
  border-radius: 8px;

  color: #fff;
  font-size: 18px;
  font-weight: 700;

  box-shadow: 3px 3px rgba(0, 0, 0, 0.4);
  transition: all 0.4s ease-out;

  /*&:hover {
  
 }*/
}

.button:hover {
  box-shadow: 6px 6px rgba(0, 0, 0, 0.6);
}

.modal-overlay {
  position: fixed;
  width: 100%;
  height: 100vh;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 98;
  background-color: rgba(0, 0, 0, 0.3);
}

.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 99;

  width: 100%;
  max-width: 400px;
  background-color: #fff;
  border-radius: 16px;

  padding: 25px;

  h1 {
    color: #222;
    font-size: 32px;
    font-weight: 900;
    margin-bottom: 15px;
  }

  p {
    color: #666;
    font-size: 18px;
    font-weight: 400;
    margin-bottom: 15px;
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.slide-enter-active,
.slide-leave-active {
  transition: transform 0.5s;
}

.slide-enter,
.slide-leave-to {
  transform: translateY(-50%) translateX(100vw);
}
</style>