<template>
  <div :class="classComputed">
    <DeleteIcon v-if="value == 'Backspace'"/>
    <MutiplyIcon v-else-if="value == '*'"/>
    <template v-else>{{ value }}</template>
  </div>
</template>

<script>
import DeleteIcon from './DeleteIcon.vue';
import MutiplyIcon from './MultiplyIcon.vue';

export default {
  name: 'ButtonComponent',
  components: {
    DeleteIcon,
    MutiplyIcon
},
  props: {
    value: String
  },
  computed: {
    classComputed() {
      let initialClass = {
        'cl-btn': true,
        'cl-btn-white': false,
        'cl-btn-grey': false,
        'cl-btn-blue': false
      }
      let whiteBtns = ['C', '%', 'Backspace', '7', '8', '9', '4', '5', '6', '1', '2', '3', '00', '0', '.'];
      let greyBtns = ['/', '*', '-', '+'];
      if (whiteBtns.includes(this.value)) {
        initialClass['cl-btn-white'] = true;
      } else if (greyBtns.includes(this.value)) {
        initialClass['cl-btn-grey'] = true;
      } else if (this.value == '=') {
        initialClass['cl-btn-blue'] = true;
      }
      return initialClass;
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

.cl-btn {
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Roboto', sans-serif;
}

.cl-btn:hover {
  cursor: pointer;
}

.cl-btn-white {
  background-color: #ffffff;
  color: #000000;
}

.cl-btn-white:active {
  background-color: #e6e6e6;
}

.cl-btn-grey {
  background-color: #e6e6e6;
  color: #000000;
}

.cl-btn-blue {
  background-color: #0066ff;
  color: #ffffff;
}

@media screen and (min-width: 1024px) {
  .cl-btn {
    width: 60px;
    height: 60px;
    font-size: 20px;
  }

  .cl-btn-grey:active, .cl-btn-blue:active {
    width: 50px;
    height: 50px;
  }
}

@media screen and (min-width: 320px) and (max-width: 425px) {
  .cl-btn {
    width: 60px;
    height: 60px;
    font-size: 20px;
  }

  .cl-btn-grey:active, .cl-btn-blue:active {
    width: 50px;
    height: 50px;
  }
}
</style>