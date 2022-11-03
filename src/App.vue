<template>
  <div id="main-wrap">
    <DisplayComponent ref="displayComponent"/>
    <div id="buttons-wrap">
      <ButtonComponent v-for="(value, key) in values" :key="key" :value="value" @click="passBtnValue(value)"/>
    </div>
  </div>
</template>

<script>
import DisplayComponent from './components/DisplayComponent.vue';
import ButtonComponent from './components/ButtonComponent.vue';

export default {
  name: 'App',
  components: {
    DisplayComponent,
    ButtonComponent
  },
  mounted() {
    window.addEventListener('keydown', this.kbHandler);
  },
  beforeUnmount() {
    window.removeEventListener('keydown', this.kbHandler);
  },
  data() {
    return {
      values: ['C', '%', 'Backspace', '/', '7', '8', '9', '*', '4', '5', '6', '-', '1', '2', '3', '+', '00', '0', '.', '='],
      btnValue: null
    }
  },
  methods: {
    passBtnValue(v) {
      switch(v) {
        case 'C': 
          this.$refs.displayComponent.clearAll();
          break;
        case 'Backspace':
          this.$refs.displayComponent.deleteLast();
          break;
        case '=':
          this.$refs.displayComponent.calculate();
          break;
        default:
          this.$refs.displayComponent.validation(v);
      }
    },
    kbHandler(e) {
      if (this.values.includes(e.key)) {
        this.passBtnValue(e.key);
      }
    }
  }
}
</script>

<style>
body {
  display: flex;
  justify-content: center;
  margin: 0;
}

@media screen and (min-width: 1024px) {
  #main-wrap {
    margin-top: 100px;
    width: 300px;
    height: 550px;
    box-sizing: border-box;
  }

  #buttons-wrap {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(5, 70px);
    align-items: center;
    justify-items: center;
  }
}

@media screen and (min-width: 320px) and (max-width: 425px) {
  #main-wrap {
    width: 100vw;
    height: 550px;
    box-sizing: border-box;
  }

  #buttons-wrap {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(5, 70px);
    align-items: center;
    justify-items: center;
  }
}
</style>