<template>
  <div id="main-wrap">
    <div id="display-last-operation"></div>
    <div id="display-result-wrap">
      <div id="display-result"></div>
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
@media screen and (min-width: 1024px) {
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

  #display-last-operation {
    width: 100%;
    height: 150px;
    background-color: #d9d9d9;
  }

  #display-result-wrap {
    padding: 8px;
    width: 100%;
    height: 50px;
    box-sizing: border-box;
    background-color: #d9d9d9;
  }

  #display-result-active {
    border-right: 2px solid #000000;
    width: 100%;
    height: 100%;
    box-sizing: border-box;
    background-color: #d9d9d9;
  }

  #display-result {
    width: 100%;
    height: 100%;
    box-sizing: border-box;
    background-color: #d9d9d9;
    animation: cursor 1s linear infinite;
  }

  @keyframes cursor {
    from { border-right: 2px solid #000000; }
    to {}
  }
}
</style>