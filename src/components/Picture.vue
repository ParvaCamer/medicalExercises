<template>
  <div class="picture">
    <div
      class="exercisePicture"
      v-for="picture in pictures"
      :key="picture.id"
      v-show="picture.id == randomNumber"
    >
      <h2>{{ picture.name }}</h2>
      <img :src="require('@/assets/images/picture' + (picture.nbCorrection-1) + '.png')" v-show="!showCorrection" class="imgExo"/>
      <img :src="require('@/assets/images/picture' + picture.nbCorrection + '.png')" v-show="showCorrection" class="imgExo" />
      <div class="showAnswer" v-if="questionNumber > picture.answers.length">
        <span> Tu as faux à :</span>
        <p class="pAnswer" v-for="(showAnswer, index) in showCorrectAnswer" :key="showAnswer.index">{{ index + 1}}/ {{ showAnswer }} </p>
      </div>
      <div class="showHelp" v-show="!showHelp && questionNumber <= picture.answers.length">
        <span>Voici les propositions :</span>
        <p class="pHelp" v-for="forHelp in answersForHelp" :key="forHelp.id"> - {{ forHelp }} </p>
      </div>
      <div class="divAnswer">
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
        <a class="round-button" v-show="showHelp && questionNumber <= picture.answers.length" @click="sendingHelp">Aide</a>
        <p v-if="questionNumber > picture.answers.length">Ton score est de {{ score }} / {{ picture.answers.length }}</p>
        <button class="btnAnswer" @click="next" v-show="questionNumber <= picture.answers.length && exerciceDone.length <= pictures.length"> Suivant </button>
        <button class="btnAnswer" @click="newTest" v-show="questionNumber > picture.answers.length && show == false"> Prochain test</button>
        <button class="btnAnswer" v-show="show == true" @click="reloadPicture">Recommencer le test</button>
        <button id="btnCorrection" class="btnAnswer" @click="correction" v-show="questionNumber > picture.answers.length"> Correction</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    pictures: Array
  },
  data() {
    return {
      randomNumber: null,
      exerciceDone: [],
      answerWrote: "",
      questionNumber: 1,
      numberAnswer: 0,
      score: 0,
      showCorrectAnswer: [],
      show: false,
      showCorrection : false,
      answersForHelp: [],
      showHelp: true
    };
  },
  mounted() {
    this.randomNumber = Math.floor(Math.random() * this.pictures.length);
    this.exerciceDone.push(this.randomNumber)
  },
  methods: {
    next() {
      let array = this.pictures[this.randomNumber].answers[this.numberAnswer].correctAnswer
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
      if (this.exerciceDone.length === this.pictures.length && this.questionNumber > this.pictures[this.randomNumber].answers.length) {
        this.show = true
      }   
    },
    newTest() {
      while (this.exerciceDone.includes(this.randomNumber) == true)  {
        this.randomNumber = Math.floor(Math.random() * this.pictures.length);
      }
      this.exerciceDone.push(this.randomNumber)
      this.numberAnswer = 0;
      this.questionNumber = 1;
      this.score = 0;
      this.showCorrectAnswer = []
      this.showCorrection = false
      this.showHelp = true
    },
    correction() {
      this.showCorrection = true
    },
    reloadPicture() {
      this.exerciceDone = []
      this.randomNumber = Math.floor(Math.random() * this.pictures.length);
      this.exerciceDone.push(this.randomNumber)
      this.numberAnswer = 0;
      this.questionNumber = 1;
      this.score = 0;
      this.showCorrectAnswer = []
      this.showCorrection = false
      this.show = false
    },
    sendingHelp() {
      this.showHelp = !this.showHelp
      this.answersForHelp = []
      let k = null;
      for (let i  = 0; i < this.pictures[this.randomNumber].answers.length; i++) {
        this.answersForHelp.push(this.pictures[this.randomNumber].answers[i].correctAnswer[1])
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
.exercisePicture {
  text-align: center;
}
.spanAnswer {
  height: 20px;
  margin-left: 1%;
  margin-top: 1%;
}
.forInput label {
  position: relative;
  font-size: 16px;
  color: #797979(0, 0, 0);
  pointer-events: none;
}
.forInput input {
  border: 0;
  border-bottom: 1px solid #555;
  background: transparent;
  padding: 8px 0 5px 0;
  font-size: 16px;
  color: #797979;
}
.forInput input:focus {
  border: none;
  outline: none;
  border-bottom: 1px solid #017ed1;
}
.imgExo {
  position: relative;
}
h2 {
  text-align: center;
  margin-bottom: 2%;
}
.btnAnswer {
  position: relative;
  margin-top: 1%;
  background: rgb(255, 255, 255);
}
#btnCorrection {
  margin-left: 2%;
}
.pAnswer {
  text-align: left;
}
.showAnswer {
  position: absolute;
  top: 50px;
  left: 13%;
  border: 2px solid black;
  padding: 8px;
  background-color: #3d3d3da2;
  color: rgb(190, 190, 190);
}
</style>