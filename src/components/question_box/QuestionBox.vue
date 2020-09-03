<template>
  <!--questionBox-->
  <section class="questionBox">
    <!-- transition -->
    <transition mode="out-in">
      <!-- qusetionContainer -->
      <div
        class="questionContainer"
        v-if="questionIndex<quiz.questions.length"
        v-bind:key="questionIndex"
      >
        <!-- <header> -->
        <Header :quiz="quiz" :questionIndex="questionIndex"></Header>
        <!-- </header> -->

        <!-- questionTitle -->
        <h2 class="titleContainer title">{{ quiz.questions[questionIndex].text }}</h2>

        <!-- quizOptions -->
        <div class="optionContainer">
          <RadioButton
            class="option"
            v-for="(answer, index) in quiz.questions[questionIndex].answers"
            name="options"
            :label="answer.text"
            @change="selectOption(index)"
            :class="{ 'is-selected': userResponses[questionIndex] == index}"
            :key="index"
          >{{ answer.text }}</RadioButton>
        </div>

        <!-- quizFooter: navigation and progress -->
        <Footer
          :quiz="quiz"
          :questionIndex="questionIndex"
          :userResponses="userResponses"
          :next="next"
          :prev="prev"
        ></Footer>
        <!--/quizFooter-->
      </div>
      <!--/questionContainer-->

      <!--quizCompletedResult-->
      <div
        v-if="questionIndex >= quiz.questions.length"
        v-bind:key="questionIndex"
        class="quizCompleted has-text-centered"
      >
        <Result :quiz="quiz" :score="score" :restart="restart"></Result>
      </div>
      <!--/quizCompetedResult-->
    </transition>
    <!--/questionBox-->
  </section>
</template>


<script>
import Header from "./Header";
import Footer from "./Footer";
import Result from "./Result";
import RadioButton from "./RadioButton";

export default {
  name: "QuestBox",
  props: ["timerEvent", "quizObject"],
  data: function () {
    return {
      quiz: this.quizObject,
      questionIndex: 0,
      userResponses: this.quizObject
        ? Array(this.quizObject.questions.length).fill(null)
        : null,
      isActive: false,
    };
  },
  components: { Header, Footer, Result, RadioButton },
  filters: {
    charIndex: function (i) {
      return String.fromCharCode(97 + i);
    },
  },
  methods: {
    restart: function () {
      this.questionIndex = 0;
      this.userResponses = Array(this.quiz.questions.length).fill(null);
      this.restartTimer();
    },
    selectOption: function (index) {
      // console.log(this.userResponses);
      this.$set(this.userResponses, this.questionIndex, index);
    },
    changeValue: function (newValue) {
      // this.selectedLabel = newValue;
    },
    next: function () {
      if (this.questionIndex < this.quiz.questions.length) this.questionIndex++;
      if (this.questionIndex >= this.quiz.questions.length) this.stopTimer();
      // ---------------------????????????----------------------------------------------------------------------
    },

    prev: function () {
      if (this.quiz.questions.length > 0) this.questionIndex--;
    },
    // Return "true" count in userResponses
    score: function () {
      var score = 0;
      for (let i = 0; i < this.userResponses.length; i++) {
        if (
          typeof this.quiz.questions[i].answers[this.userResponses[i]] !==
            "undefined" &&
          this.quiz.questions[i].answers[this.userResponses[i]].correct
        ) {
          score = score + 1;
        }
      }
      return score;

      //return this.userResponses.filter(function(val) { return val }).length;
    },
    restartTimer: function () {
      this.timerEvent("restart");
    },
    stopTimer: function () {
      this.timerEvent("stop");
    },
  },
};
</script>

<style >
.button {
  transition: 0.5s;
}
.title,
.subtitle {
  font-family: Montserrat, sans-serif;
  font-weight: normal;
}

.titleContainer {
  text-align: center;
  margin: 0 auto;
  padding: 1.5rem;
}

.questionContainer {
  white-space: normal;
  height: 100%;
  width: 100%;
}
.optionContainer {
  margin-top: 12px;
  flex-grow: 1;
}
.option {
  transition: 0.3s;
}
.option.is-selected {
  border-color: rgba(0, 0, 0, 0.25);
}

.option:active {
  transform: scaleX(0.9);
}
.questionBox .quizCompleted {
  width: 100%;
  padding: 1rem;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
}

@media screen and (min-width: 769px) {
  .questionBox {
    align-items: center;
    justify-content: center;
  }
  .questionBox .questionContainer {
    display: flex;
    flex-direction: column;
  }
}
@media screen and (max-width: 768px) {
  .questionBox {
    margin: 0px 5px 0px 5px;
    z-index: 2;
  }
  .sidebar {
    height: auto !important;
    border-radius: 6px 6px 0px 0px;
  }
}
</style>