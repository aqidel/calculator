<template>
  <div class="cl-button" :style="computedStyle">{{ value }}</div>
</template>

<script>
export default {
  name: 'ButtonComponent',
  props: {
    value: String
  },
  computed: {
    computedStyle() {
      let style = {
        backgroundColor: "#ffffff",
        color: "#000000"
      };
      if (['0', '00', '1', '2', '3', '4', '5', '6', '7', '8', '9', ',', '%', 'C', 'DEL'].includes(this.value)) {
        style.backgroundColor = "#ffffff";
      } else if (['/', '*', '-', '+'].includes(this.value)) {
        style.backgroundColor = "#e6e6e6";
      } else if (this.value == '=') {
        style.backgroundColor = "#0066ff";
        style.color = "#ffffff";
      }
      return style;
    }
  }
}
</script>

<style scoped>
@media screen and (min-width: 1024px) {
  @import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
  .cl-button {
    border-radius: 50%;
    width: 60px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    font-family: 'Roboto', sans-serif;
  }
}
</style>