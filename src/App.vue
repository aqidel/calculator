<template>
  <div id="main-wrap">
    <div id="display-last-operation"></div>
    <div id="display-result-wrap">
      <div id="display-result"></div>
    </div>
    <div id="buttons-wrap">
      <ButtonComponent v-for="(value, key) in values" :key="key" :value="value"/>
    </div>
  </div>
</template>

<script>
import ButtonComponent from './components/ButtonComponent.vue'

export default {
  name: 'App',
  components: {
    ButtonComponent
  },
  data() {
    return {
      values: ["C", "%", "DEL", "/", "7", "8", "9", "x", "4", "5", "6", "-", "1", "2", "3", "+", "00", "0", ",", "="]
    }
  }
}
</script>

<style>
@media screen and (min-width: 1024px) {
  body {
  display: flex;
  justify-content: center;
  margin: 0;
  }

  #main-wrap {
    margin-top: 100px;
    width: 300px;
    height: 550px;
    box-sizing: border-box;
  }

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
    box-sizing: border-box;
    background-color: #e6e6e6;
    animation: cursor 1s linear infinite;
  }

  @keyframes cursor {
    from { border-right: 2px solid #000000; }
    to {}
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