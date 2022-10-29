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
  methods: {
    validation(v) {}
    /*validation(v) {
      // Can't be shown at display at all
      if (v == 'C' || v == 'DEL' || v == '=') {
        return null;
      }
      // Only 0-1, '-' can be first symbol 
      if (this.expression.length == 0 && ['%', '/', '*', '+', '00', ','].includes(v)) {
        return null;
      }
      // 0 can't follow after other 0 except for after '0,'
      if (this.expression == '0' && v == '0') {
        return null;
      }
      this.expression = this.expression + v;
    }*/
  },
  /*computed: {
    expression() {
      return
    }
  },*/
  /*watch: {
    btnValue() {
      if (this.validation()) {
        this.expression = this.expression + this.btnValue;
      } else {
        return null;
      }
    }
  }*/
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