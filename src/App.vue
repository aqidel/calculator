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
  data() {
    return {
      values: ['C', '%', 'DEL', '/', '7', '8', '9', '*', '4', '5', '6', '-', '1', '2', '3', '+', '00', '0', ',', '='],
      btnValue: null
    }
  },
  methods: {
    passBtnValue(v) {
      this.$refs.displayComponent.validation(v);
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

  #buttons-wrap {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(5, 70px);
    align-items: center;
    justify-items: center;
  }
}
</style>