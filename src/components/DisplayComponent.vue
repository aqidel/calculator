<template>
  <div id="display-last-operation"></div>
    <div id="display-result-wrap">
      <div id="display-result">{{ displayedExpression }}</div>
    </div>
</template>

<script>
export default {
  name: 'DisplayComponent',
  props: ['btnValue'],
  data() {
    return {
      displayedExpression: '',
      calculatedExpression: ''
    }
  },
  methods: {
    validation(v) {
      let tempExpression = this.displayedExpression + v;
      if (/^((-?)((0|((0\.|[1-9](\d+)?\.)(\d+)?)|([1-9](\d+)?))([%*/+-]?))?)+$/g.test(tempExpression)) {
        // regexp doesn't work properly, so a couple of bugfixes here
        if (tempExpression.endsWith('--')) {
          return null;
        }
        else if (/^.+[*+/]-$/g.test(tempExpression)) {
          return null;
        }
        else if (/^.+(\d+\.\d+\.)$/g.test(tempExpression)) {
          return null;
        }
        else {
          this.displayedExpression = tempExpression;
        }
      } else {
        return null;
      }
    },
    clearAll() {
      this.displayedExpression = '';
    },
    deleteLast() {
      this.displayedExpression = this.displayedExpression.slice(0, -1);
    },
    calculate() {
      this.calculatedExpression = this.displayedExpression;
      while (this.calculatedExpression.includes('%')) {
        let replaced = this.calculatedExpression.replace('%', '*0.01');
        this.calculatedExpression = replaced;
      }
      this.displayedExpression = eval(this.calculatedExpression);
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