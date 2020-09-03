<template>
  <header>
    <h1 class="title is-6">VueQuiz</h1>
    <!--progress-->
    <div class="progressContainer">
      <progress
        class="progress is-info is-small"
        :value="(questionIndex/quiz.questions.length)*100"
        max="100"
      >{{(questionIndex/quiz.questions.length)*100}}%</progress>
      <p>{{(questionIndex/quiz.questions.length)*100}}% complete</p>
    </div>
    <!--/progress-->
  </header>
</template>
<script>
export default {
  props: ["quiz", "questionIndex"],
  name: "Header",
};
</script>
<style>
.questionBox {
  max-width: 30rem;
  width: 30rem;
  min-height: 30rem;
  background: #fafafa;
  position: relative;
  display: flex;
  border-radius: 0.5rem;
  overflow: hidden;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
}
.questionBox header {
  background: rgba(0, 0, 0, 0.025);
  padding: 1.5rem;
  text-align: center;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}
.questionBox header h1 {
  font-weight: bold;
  margin-bottom: 1rem !important;
}
.questionBox header .progressContainer {
  width: 60%;
  margin: 0 auto;
}
.questionBox header .progressContainer > progress {
  margin: 0;
  border-radius: 5rem;
  overflow: hidden;
  border: none;
  color: #3d5afe;
}
.questionBox header .progressContainer > progress::-moz-progress-bar {
  background: #3d5afe;
}
.questionBox header .progressContainer > progress::-webkit-progress-value {
  background: #3d5afe;
}
.questionBox header .progressContainer > p {
  margin: 0;
  margin-top: 0.5rem;
}
</style>