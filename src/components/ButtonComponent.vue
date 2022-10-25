<template>
  <div :class="computedBtnClass">{{ value }}</div>
</template>

<script>
export default {
  name: 'ButtonComponent',
  props: {
    value: String
  },
  computed: {
    computedBtnClass() {
      let classObject = {
        'cl-button': true,
        'cl-button-white': false,
        'cl-button-grey': false,
        'cl-button-blue': false
      };
      if (['0', '00', '1', '2', '3', '4', '5', '6', '7', '8', '9', ',', '%', 'C', 'DEL'].includes(this.value)) {
        classObject['cl-button-white'] = true;
      } else if (['/', 'x', '-', '+'].includes(this.value)) {
        classObject['cl-button-grey'] = true;
      } else if (this.value == '=') {
        classObject['cl-button-blue'] = true;
      }
      return classObject;
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

  .cl-button:hover {
    cursor: pointer;
  }

  .cl-button-white {
    background-color: #ffffff;
    color: #000000;
  }

  .cl-button-white:active {
    background-color: #e6e6e6;
  }

  .cl-button-grey {
    background-color: #e6e6e6;
    color: #000000;
  }

  .cl-button-blue {
    background-color: #0066ff;
    color: #ffffff;
  }

  .cl-button-grey:active, .cl-button-blue:active {
    width: 50px;
    height: 50px;
  }
}
</style>