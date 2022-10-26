<template>
  <div id="display-last-operation"></div>
    <div id="display-result-wrap">
      <div id="display-result">{{ expression }}</div>
    </div>
</template>

<script>
export default {
  name: 'DisplayComponent',
  props: ['btnValue'],
  data() {
    return {
      expression: ''
    }
  },
  watch: {
    btnValue() {
      this.expression = this.expression + this.btnValue
    }
  }
}
</script>

<style scoped>
@media screen and (min-width: 1024px) {
  @import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

  #display-last-operation {
    width: 100%;
    height: 150px;
    background-color: #e6e6e6;
  }

  #display-result-wrap {
    padding: 8px;
    width: 100%;
    height: 50px;
    box-sizing: border-box;
    background-color: #e6e6e6;
  }

  #display-result-active {
    border-right: 2px solid #000000;
    width: 100%;
    height: 100%;
    box-sizing: border-box;
    background-color: #e6e6e6;
  }

  #display-result {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: flex-end;
    align-items: flex-end;
    background-color: #e6e6e6;
    animation-name: cursor;
    animation-duration: 1s;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
    animation-play-state: running;
    font-family: 'Roboto', sans-serif;
    font-size: 30px;
  }

  @keyframes cursor {
    0% { border-right: 2px solid #000000; }
    100% {}
  }
}
</style>