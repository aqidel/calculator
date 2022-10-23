<template>
  <div id="main-wrap">
    <div id="display-wrap">
      <div id="display"></div>
    </div>
  </div>
</template>

<script>
//import ButtonComponent from './components/ButtonComponent.vue'

export default {
  name: 'App',
  components: {
    //ButtonComponent
  }
}
</script>

<style>
body {
  display: flex;
  justify-content: center;
  margin: 0;
}

#main-wrap {
  margin-top: 100px;
  border: 1px solid #000000;
  width: 400px;
  height: 600px;
}

#display-wrap {
  padding-bottom: 20px;
  width: 100%;
  height: 200px;
  box-sizing: border-box;
  background-color: aquamarine;
}
</style>