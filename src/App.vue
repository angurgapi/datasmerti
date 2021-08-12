<template>
<div class="page-wrapper">
  <Header />
  <CentralBlock />
  <QuestionBlock />
  <div class="shine-bg"></div>
</div>
</template>

<script>

import Header from './components/Header.vue'
import CentralBlock from './components/CentralBlock.vue'
import QuestionBlock from './components/QuestionBlock.vue'

export default {
  name: 'App',
  components: {
    Header,
    CentralBlock,
    QuestionBlock
  },
  data(){
    return {
      currentQuestion: 0,
      questions: [{name: 'Боитесь ли вы умереть?', number: '1'}]
    }
  }
}
</script>

<style lang='sass'>
@font-face
    font-family: "Roboto"
    src: local("Roboto"), url(./assets/fonts/Roboto-Light.ttf) format("truetype")
@font-face
    font-family: "Roboto-Regular"
    src: local("Roboto-Regular"), url(./assets/fonts/Roboto-Regular.ttf) format("truetype")
@font-face
    font-family: "BadScript"
    src: local("BadScript"), url(./assets/fonts/BadScript.ttf) format("truetype")
.page-wrapper 
  min-width: 100%
  height: 100%
.shine-bg
  background: url('./assets/img/blik-crop.png')
  background-size: cover
  width: 100%
  height: 900px
  position: absolute
  top: 0
  z-index: -10
</style>
