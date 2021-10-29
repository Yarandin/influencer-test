<template>
  <div id="app">
    <Header/>
    <TabWrapper />
  </div>
</template>

<script>
import Header from './components/Header/Header'
import TabWrapper from './components/TabWrapper/TabWrapper.vue'

export default {
  name: 'App',
  components: {
    Header, TabWrapper
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@500&family=Nunito+Sans:wght@400;600;700;800&display=swap');
  @font-face {
    font-family: "SegoeUIBlack";
    src: local("SegoeUIBlack"),
    url(./fonts/SegoeUIBlack/seguibl.ttf) format("truetype");
  }
  #app {
    display: flex;
    flex-direction: column;
    align-items: center;
    background: rgb(243 243 246);
    width: 100%;
    height: auto;
    font-family: 'Nunito Sans', sans-serif;
  }
  .btn {
    background: none;
    color: inherit;
    border: none;
    padding: 0;
    font: inherit;
    cursor: pointer;
    outline: inherit;
  }
  .p {
    margin: 0;
    padding: 0;
  }
  body {
    margin: 0;
  }
</style>
