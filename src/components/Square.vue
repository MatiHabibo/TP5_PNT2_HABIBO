<template>
  <section class="src-components-square">
    <div
      class="square"
      @click="getColor()"
      :class="isWrong && 'displayNone'"
      :style="{ 'background-color': isWrong ? '#232323' : color }"
    ></div>
  </section>
</template>

<script>
export default {
  name: "src-components-square",
  props: ["color", "pickedColor"],
  mounted() {},
  data() {
    return {
      isWrong: false,
    };
  },
  methods: {
    getColor() {
      let msg = "";
      if (this.pickedColor === this.color) {
        msg = "You win";
        this.isWrong = false;
      } else {
        msg = "Choose another color";
        this.isWrong = true;
      }
      this.$parent.$emit("selectedColor", this.color);
      this.$parent.$emit("message", msg);
    },
  },
  computed: {},
};
</script>

<style scoped lang="css">
.src-components-square {
}
.displayNone {
  background-color: #232323;
}
.square {
  width: 30%;
  background: blue;
  padding-bottom: 30%;
  float: left;
  margin: 1.66%;
  border-radius: 10%;
  transition: background 0.8s;
  -webkit-transition: background 0.8s;
  -moz-transition: background 0.8s;
}
</style>
