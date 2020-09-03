<template>
  <!--quizCompletedResult-->
  <div>
    <!-- quizCompletedIcon: Achievement Icon -->
    <span class="icon">
      <i class="fa" :class="score()>3?'fa-check-circle-o is-active':'fa-times-circle'"></i>
    </span>

    <!--resultTitleBlock-->
    <h2 class="title">
      Вы проделали {{ (score()>7?'потрясающую':(score()<4?'плохую':'хорошую'))
      }} работу!
    </h2>
    <p class="subtitle">Правильных ответов: {{ score() }} / {{ quiz.questions.length }}</p>
    <br />
    <a class="button" @click="restart()">
      restart
      <i class="fa fa-refresh"></i>
    </a>
    <!--/resultTitleBlock-->
  </div>
  <!--/quizCompetedResult-->
</template>
<script>
export default {
  props: ["quiz", "score", "restart"],
  data: function () {
    return {};
  },
  methods: {
    scorePro() {
      return this.score();
    },
    restartPro() {
      return this.restart();
    },
  },
};
</script>
<style>
.icon {
  color: #ff5252;
  font-size: 5rem;
}
.is-active {
  color: #00e676;
}
</style>