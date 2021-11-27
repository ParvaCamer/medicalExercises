<template>
  <div class="pictureList">
    <div v-show="!showPicture">
      <template v-for="picture in pictures" :key="picture.id">
        <span v-if="limitList - 2 <= picture.id && picture.id <= limitList">
          <img :src="require('@/assets/images/picture' +(picture.nbCorrection - 1) +'.png')" class="imgList" @click="openPic(picture.id)"
          />
        </span>
      </template>
      <button class="arrow left" @click="previousPic" v-show="limitList >= 3">
        <svg
          width="60px"
          height="80px"
          viewBox="0 0 50 80"
          xml:space="preserve"
        >
          <polyline
            fill="none"
            stroke="#FFFFFF"
            stroke-width="1"
            stroke-linecap="round"
            stroke-linejoin="round"
            points="45.63,75.8 0.375,38.087 45.63,0.375 "
          />
        </svg>
      </button>
      <button
        class="arrow right"
        @click="nextPic"
        v-show="limitList < pictures.length -1"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          width="60px"
          height="80px"
          viewBox="0 0 50 80"
          xml:space="preserve"
        >
          <polyline
            fill="none"
            stroke="#FFFFFF"
            stroke-width="1"
            stroke-linecap="round"
            stroke-linejoin="round"
            points="0.375,0.375 45.63,38.087 0.375,75.8 "
          />
        </svg>
      </button>
    </div>
    <div
      class="divExoPic"
      v-show="showPicture && picture.id == valueShowPicture"
      v-for="picture in pictures"
      :key="picture.id"
    >
      <img v-show="valueShowPicture === picture.id && !showCorrection" :src="require('@/assets/images/picture' +(picture.nbCorrection - 1) +'.png')" class="imgOnePic"/>
      <img :src="require('@/assets/images/picture' + picture.nbCorrection + '.png')" v-show="showCorrection" class="imgOnePic" />
      <div class="showAnswer" v-if="questionNumber > picture.answers.length">
        <span> Tu as faux à :</span>
        <p class="pAnswer" v-for="showAnswer in showCorrectAnswer" :key="showAnswer.index">- {{ showAnswer }} </p>
      </div>
      <div class="showHelp" v-show="!showHelp && questionNumber <= picture.answers.length">
        <span>Voici les propositions :</span>
        <p class="pHelp" v-for="forHelp in answersForHelp" :key="forHelp.id"> - {{ forHelp }} </p>
      </div>
      <div
        class="forInput"
        v-for="answer in picture.answers"
        :key="answer.number"
      >
        <span v-if="answer.number === questionNumber">
          <label> Réponse n°{{ answer.number }} : </label>
          <input class="spanAnswer" v-model="answerWrote" />
        </span>
      </div>
      <a class="round-button" v-show="showHelp && questionNumber <= picture.answers.length" @click="sendingHelp()">Aide</a>
      <p class="pScore" v-if="questionNumber > picture.answers.length">Ton score est de {{ score }} / {{ picture.answers.length }}</p>
      <button class="btnAnswer" @click="next" v-show="questionNumber <= picture.answers.length && exerciceDone.length <= pictures.length">Suivant</button>
      <button class="btnAnswer" @click="newTest" v-show="questionNumber > picture.answers.length">Prochain test</button>
      <button id="btnCorrection" class="btnAnswer" @click="correction" v-show="questionNumber > picture.answers.length">Correction</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    pictures: Array,
  },
  data() {
    return {
      limitList: 2,
      valueShowPicture: null,
      showPicture: false,
      exerciceDone: [],
      answerWrote: "",
      questionNumber: 1,
      numberAnswer: 0,
      score: 0,
      showCorrectAnswer: [],
      showCorrection: false,
      answersForHelp: [],
      showHelp: true
    };
  },
  methods: {
    previousPic() {
      this.limitList -= 3;
    },
    nextPic() {
      this.limitList += 3;
    },
    openPic(value) {
      this.valueShowPicture = value;
      this.showPicture = true;
    },
    next() {
      let array = this.pictures[this.valueShowPicture].answers[this.numberAnswer].correctAnswer
      if ((array.includes(this.answerWrote)) && (this.answerWrote !== "")) {
        this.score++;
      } else {
        this.showCorrectAnswer.push(array[1])
      }
      let array2 = this.answersForHelp
      if (!this.showHelp) {
        for (let i = 0; i < array.length; i++) { //array correctAnswer
          for (let j = 0; j < array2.length; j++) { //array help
            if (array[i] === array2[j] && this.answerWrote !== "" && array.includes(this.answerWrote)) {
              this.answersForHelp.splice(j, 1)
            }
          }
        }
      }
      this.answerWrote = "";
      this.numberAnswer++;
      this.questionNumber++;
    },
    newTest() {
      this.numberAnswer = 0;
      this.questionNumber = 1;
      this.score = 0;
      this.showCorrectAnswer = [];
      this.showCorrection = false;
      this.showPicture = false;
      this.showHelp = true;
    },
    correction() {
      this.showCorrection = true;
    },
    sendingHelp() {
      this.showHelp = !this.showHelp
      this.answersForHelp = []
      let k = null;
      for (let i  = 0; i < this.pictures[this.valueShowPicture].answers.length; i++) {
        this.answersForHelp.push(this.pictures[this.valueShowPicture].answers[i].correctAnswer[1])
      }
      for (let i = this.answersForHelp.length-1; i > 0; i--) {
        var j=Math.floor(Math.random()*(i+1));
        k = this.answersForHelp[i]
        this.answersForHelp[i] = this.answersForHelp[j];
        this.answersForHelp[j] = k
      }
    }
  },
};
</script>

<style>
.pictureList {
  text-align: center;
  margin-left: 4%;
  margin-top: 130px;
}
.imgList {
  position: sticky;
  margin-right: 4%;
}
.imgOnePic{
  margin-top: -70px;
}

button {
  -webkit-appearance: none;
  background: transparent;
  border: 0;
  outline: 0;
}

svg {
  padding: 5px;
}

.arrow {
  cursor: pointer;
  position: absolute;
  top: 50%;
  margin-top: -45px;
  margin-left: -35px;
  width: 70px;
  height: 90px;
}

.left {
  left: 20%;
}

.left:hover polyline,
.left:focus polyline {
  stroke-width: 3;
}

.left:active polyline {
  stroke-width: 6;
  transition: all 100ms ease-in-out;
}

.right:hover polyline,
.right:focus polyline {
  stroke-width: 3;
}

.right:active polyline {
  stroke-width: 6;
  transition: all 100ms ease-in-out;
}

polyline {
  transition: all 250ms ease-in-out;
}
.pScore {
  margin-top: 23px;
}
.showHelp {
  position: absolute;
  top: 50px;
  left: 76%;
  border: 2px solid black;
  padding: 8px;
  background-color: #3d3d3da2;
  color: rgb(190, 190, 190);
  text-align: left;
}
.round-button {
    position: absolute;
    width:41px;
    height:41px;
    line-height:41px;
    border: 2px solid #f5f5f5;
    border-radius: 50%;
    color:#f5f5f5;
    text-align:center;
    text-decoration:none;
    background: #555777;
    box-shadow: 0 0 8px rgb(255, 255, 255);
    font-size:15px;
    font-weight:bold;
    top: 90%;
    left: 80%;
}
.round-button:hover {
    background: #454663;
}
</style>