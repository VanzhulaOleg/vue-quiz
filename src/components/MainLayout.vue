<template>
  <div class="main-container">
    <Timer :timerEvent="timer"></Timer>
    <Question-box :timerEvent="timerEvent" :quizObject="quizObject"></Question-box>
  </div>
</template>
<script>
import Timer from "./Timer.vue";
import QuestionBox from "./question_box/QuestionBox.vue";

var quiz = {
    user: "Skiff",
    questions: [
      {
        text: "Что такое Vue.js?",
        answers: [
          { text: "Это расширение JavaScript" },
          { text: "Это фреймворк JavaScript", correct: true },
          { text: "Это дополнительные возможности JavaScript" },
          { text: "Это библиотека JavaScript" },
        ],
      },
      {
        text: "Как установить атрибут title у тега p?",
        answers: [
          { text: "<p title='{{text}}'>Текст</p>" },
          { text: "<p title='text'>Текст</p>" },
          { text: "<p :title='{{text}}'>Текст</p>" },
          { text: "<p v-title='text'>Текст</p>" },
          { text: "<p :title='text'>Текст</p>", correct: true },
        ],
      },
      {
        text: "Как обратиться к переменной text в объекте?",
        answers: [
          { text: "this=>text" },
          { text: "this.text", correct: true },
          { text: "that.text" },
          { text: "this>text" },
          { text: "this->text" },
        ],
      },
      {
        text: "Какой атрибут будет вызывать событие при клике на объект?",
        answers: [
          { text: "<span v-on-click='change'>Текст</span>" },
          { text: "<span @click='change'>Текст</span>", correct: true },
          { text: "<span onclick='change'>Текст</span>" },
          { text: "<span @click='{{change}}'>Текст</span>" },
        ],
      },
      {
        text: "Где правильно создан Vue объект?",
        answers: [
          { text: "var test = Vue ({ })" },
          {
            text: "new Vue { }",
          },
          { text: "var test = new Vue { }" },
          { text: "new Vue ()" },
          { text: "var test = new Vue ({ })", correct: true },
        ],
      },
      {
        text: "Как вывести переменную message в HTML?",
        answers: [
          { text: "К тегу добавить атрибут :value='message'" },
          { text: "message" },
          { text: "{{message}}", correct: true },
          { text: "<message></message>" },
          { text: "{message}" },
        ],
      },
      {
        text: "Как получить данные из текстового поля?",
        answers: [
          { text: "$event.target.value", correct: true },
          { text: "$event.target" },
          { text: "$event.value" },
          { text: "$event.target.val" },
          { text: "$target.value" },
        ],
      },
      {
        text:
          'Как выбрать элемент через Vue.js? \n <h2 class="app" id="main"></h2>;',
        answers: [
          { text: "el: '.app'" },
          { text: "el: '#main'" },
          { text: "el: 'h2'" },
          { text: "Нельзя найти элемент, так как он не div" },
          {
            text:
              "Все способы правильные, но чтобы все работало корректно лучше искать по id",
            correct: true,
          },
        ],
      },
      {
        text:
          "Какая директива используется для создания двунаправленной привязки данных?",
        answers: [
          {
            text: "никакая",
          },
          { text: " v-inline" },
          { text: " v-model", correct: true },
          { text: " v-on" },
        ],
      },
      {
        text: "Как расшифровывается MVVM?",
        answers: [
          { text: " Model-View-ValueModel " },
          { text: " Model-View-ViewModel", correct: true },
          { text: " Modele-Value-ValueModel" },
          { text: " Module-View-ViewModel" },
        ],
      },
    ],
  },
  userResponseSkelaton = Array(quiz.questions.length).fill(null);

export default {
  name: "MainContainer",
  components: {
    Timer,
    QuestionBox,
  },
  data: function () {
    return {
      timer: false,
      quizObject: quiz,
    };
  },
  mounted() {},
  methods: {
    timerEvent: function (data) {
      // console.log("data main", data);
      this.timer = data;
    },
  },
};
</script>
<style >
.main-container {
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>