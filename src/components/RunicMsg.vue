<template>
    <div class="runic-msg">
        <div class="eye"><img class="eye-img" src="../assets/img/eye.svg" /></div>
        <img src="../assets/img/runic1.svg"/>
        <p class="handwritten">{{ messageText }}</p>
        <img src="../assets/img/runic2.svg"/>
        <div class="planet"><img class="planet-img" src="../assets/img/planet.svg" /></div>
    </div>
</template>

<script>

export default {
    name: 'RunicMsg',
    props: {
        messageText: {
            type: String
        }
    }
}
</script>

<style lang="sass">
.runic-msg
    width: 100%
    display: flex
    flex-direction: column
    justify-content: center
    align-items: center
.handwritten
    font-family: 'BadScript'
    font-size: 25px
    line-height: 35px
    color: #fff
    text-align: center
    max-width: 300px

.eye, .planet
    position: relative
    opacity: .3
    width: 100%
    top: 0
    display: flex
.eye 
    justify-content: flex-end
.planet
    justify-content: flex-start
.planet-img 
    height: 50px 
    width: 50px

</style>