<template>
  <div>
    <label class="radio">
      <input type="radio" :value="label" :name="name" v-model="radioButtonValue" />
      <span>{{ label }}</span>
    </label>
  </div>
</template>

<script>
export default {
  props: ["name", "label"],
  computed: {
    radioButtonValue: {
      set: function () {
        // Communicate the change to parent component so that selectedValue can be updated
        this.$emit("change", this.label);
      },
      get: function () {},
    },
  },
};
</script>
<style scoped>
.radio {
  display: flex;
  align-items: center;
  width: auto;
  background-color: rgba(0, 0, 0, 0.05);
  color: rgba(0, 0, 0, 0.85);
  padding: 9px 18px;
  margin: 0 18px;
  margin-bottom: 12px;
  cursor: pointer;
  border-radius: 290486px;
  border: transparent 1px solid;
}
.radio:hover {
  border-color: rgba(0, 0, 0, 0.25);
  background-color: white;
}
input {
  margin-right: 10px;
  padding-bottom: 5px;
}
</style>