<template>
  <footer class="questionFooter">
    <nav class="pagination" role="navigation" aria-label="pagination">
      <!-- back button -->
      <a class="button" v-if="questionIndex > 0" v-on:click="prevPro();">Back</a>
      <!-- next button -->
      <a
        class="button"
        :class="(userResponses[questionIndex]==null)?'':'is-active'"
        v-on:click="nextPro();"
        :disabled="questionIndex>=quiz.questions.length"
      >{{ (userResponses[questionIndex]==null)?'Skip':'Next' }}</a>
    </nav>
  </footer>
</template>
<script>
export default {
  props: ["quiz", "questionIndex", "userResponses", "next", "prev"],
  name: "Footer",
  data: function () {
    return {};
  },
  methods: {
    nextPro: function () {
      // console.log(this.questionIndex, "questionIndex footer");
      return this.next();
    },

    prevPro: function () {
      return this.prev();
    },
  },
};
</script>
<style>
.questionBox .questionContainer .questionFooter {
  background: rgba(0, 0, 0, 0.025);
  border-top: 1px solid rgba(0, 0, 0, 0.1);
  width: 100%;
  align-self: flex-end;
}
.questionBox .questionContainer .questionFooter .pagination {
  margin: 15px 25px;
}
.pagination {
  display: flex;
  justify-content: space-around;
}
.button {
  padding: 0.5rem 1rem;
  border: 1px solid rgba(0, 0, 0, 0.25);
  border-radius: 5rem;
  margin: 0 0.25rem;
  transition: 0.3s;
}
.button:hover {
  cursor: pointer;
  background: #eceff1;
  border-color: rgba(0, 0, 0, 0.25);
}
.button.is-active {
  background: #3d5afe;
  color: white;
  border-color: transparent;
}
.button.is-active:hover {
  background: #0a2ffe;
}
</style>