<template>
  <div id="app">
    <div class="wrapper clearfix">
      <Players
        v-bind:activePlayer="activePlayer"
        v-bind:scoresPlayer="scoresPlayer"
        v-bind:currentScore="currentScore"
      />

      <Controls v-on:handleNewGame="handleNewGame" />

      <Dices />

      <Popup-rule 
        v-on:handleConfirm="handleConfirm"
        v-bind:isOpenPopup="isOpenPopup"
      />
    </div>
  </div>
</template>

<script>
import Players from "./components/Players.vue";
import Controls from "./components/Controls.vue";
import Dices from "./components/Dices.vue";
import PopupRule from "./components/PopupRule.vue";
export default {
  name: "app",
  data() {
    return {
      isPlaying: false,
      isOpenPopup: false,
      activePlayer: 1, // Ai là người chơi hiện tại
      scoresPlayer: [20, 50],
      currentScore: 23,
    };
  },
  components: {
    Players,
    Controls,
    Dices,
    PopupRule,
  },
  methods: {
    handleConfirm() {
      console.log("handleConfirm App.vue");
    },
    handleNewGame() {
      console.log("handleNewGame App.vue");
      // hiện thị Popup -> show luật chơi
      this.isOpenPopup = true;
    },
  },
};
</script>

<style>
/**********************************************
*** GENERAL
**********************************************/

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.clearfix::after {
  content: "";
  display: table;
  clear: both;
}

body {
  background-image: linear-gradient(
      rgba(62, 20, 20, 0.4),
      rgba(62, 20, 20, 0.4)
    ),
    url("./public/assets/back.jpg");
  background-size: cover;
  background-position: center;
  font-family: Lato;
  font-weight: 300;
  position: relative;
  height: 100vh;
  color: #555;
}

.wrapper {
  width: 1000px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  box-shadow: 0px 10px 50px rgba(0, 0, 0, 0.3);
  overflow: hidden;
}
</style>
