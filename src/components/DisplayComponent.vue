<template>
  <div id="display-last-operation"></div>
    <div id="display-result-wrap">
      <div :id="cursorBlink" class="display-result">{{ displayedExpression }}</div>
    </div>
</template>

<script>
export default {
  name: 'DisplayComponent',
  props: ['btnValue'],
  data() {
    return {
      displayedExpression: '',
      calculatedExpression: '',
      isActive: false
    }
  },
  computed: {
    cursorBlink() {
      return this.isActive ? 'display-result-on' : 'display-result-off';
    }
  },
  methods: {
    validation(v) {
      this.blinker('on');
      let tempExpression = this.displayedExpression + v;
      if (/^((-?)((0|((0\.|[1-9](\d+)?\.)(\d+)?)|([1-9](\d+)?))([%*/+-]?))?)+$/g.test(tempExpression)) {
        // regexp doesn't work properly, so a couple of bugfixes here
        if (tempExpression.endsWith('--')) {
          this.blinker('off');
          return null;
        }
        else if (/^.+[*+/]-$/g.test(tempExpression)) {
          this.blinker('off');
          return null;
        }
        else if (/^.+(\d+\.\d+\.)$/g.test(tempExpression)) {
          this.blinker('off');
          return null;
        }
        else {
          this.blinker('off');
          this.displayedExpression = tempExpression;
        }
      } else {
        this.blinker('off');
        return null;
      }
    },
    clearAll() {
      this.displayedExpression = '';
    },
    deleteLast() {
      this.blinker('on');
      this.displayedExpression = this.displayedExpression.slice(0, -1);
      this.blinker('off');
    },
    calculate() {
      this.calculatedExpression = this.displayedExpression;
      while (this.calculatedExpression.includes('%')) {
        let replaced = this.calculatedExpression.replace('%', '*0.01');
        this.calculatedExpression = replaced;
      }
      this.displayedExpression = eval(this.calculatedExpression) + '';
    },
    blinker(cmd) {
      if (cmd == 'on') {
        this.isActive = true;
      }
      else if (cmd == 'off') {
        setTimeout(() => { this.isActive = false }, 1000);
      }
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

  .display-result {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: flex-end;
    align-items: flex-end;
    background-color: #e6e6e6;
    overflow: hidden;
    font-family: 'Roboto', sans-serif;
    font-size: 30px;
  }

  #display-result-off {
    animation-name: cursor;
    animation-duration: 1s;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
  }

  @keyframes cursor {
    0% { border-right: 2px solid #000000; }
    100% {}
  }

  #display-result-on {
    border-right: 2px solid #000000;
    background-color: #e6e6e6;
  }
}
</style>