<template>
    <div class="mic-loader">
        <img class="mic-img" src="../assets/img/microphone.svg" />
        <div class="loader">
            <div class="loader__element"></div>
        </div>
    </div>
</template>

<style lang="sass" scoped>
.mic-loader
    display: flex
    height: 300px
    flex-direction: column
    align-items: center
    justify-content: center

.loader
    margin-top: 20px
    background-color: #fff
    width: 300px
    height: 10px
    border-radius: 2px
    display: flex
    justify-content: flex-start
    align-items: center
    
.loader__element
    height: 100%
    width: 0
    background-color:  #F6C866
    animation: grow 3s ease-in infinite
    border-radius: 2px


@keyframes grow
    0%
        width: 0
    50%
        width: 50%
    100%
        width: 100%

</style>