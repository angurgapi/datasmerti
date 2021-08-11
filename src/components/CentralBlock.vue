<template>
    <div class="center-block">
        <div class="circle">
            <img class="circle__bg" src="../assets/img/Vector.png"/>
            <img class="circle__img" src="../assets/img/woman.png"/>            
        </div>
        <div class="text-block">
            <p class="text-block__text">
                Вас беспокоит вопрос о том, <br/> КОГДА ВЫ ПОКИНЕТЕ ЭТОТ МИР И ПРИ КАКИХ ОБСТОЯТЕЛЬСТВАХ?
            </p>
        </div>
        <div class="button-block">
            <button class="button-block__btn">Да</button>
            <button class="button-block__btn">Нет</button>
        </div>
        <p class="detail-text">Онлайн-предсказание</p>
        
        <div class="text-wrap">
            <div class="hands-img"><img class="hands-img" src="../assets/img/hands.png"/></div>
            <p class="text-block__text text-white">Позвольте нам раскрыть эту волнующую тайну и <span class="text-yellow"><b>с точностью определить дату и время вашей смерти,</b></span> а также предшествующую этому событию причину</p>
        </div>

        <div class="meditation">
            <div class="dimmer">
                <p class="text-block__text text-white">Многие не верят предсказаниям и мы решили доказать каждому, <span class="text-yellow">что прогноз может изменить жизнь любого человека</span> а также предшествующую этому событию причину</p>
            </div>
        </div>
    </div>
</template>

<style lang='sass'>
.center-block, .circle, .button-block, .text-wrap, .meditation, .dimmer
    font-family: 'Roboto'
    display: flex
    flex-direction: column
    align-items: center
    justify-content: center
.circle
    margin-top: 60px
    height: 345px
    width: 345px
    background-size: cover
    &__bg 
        position: absolute
        height: 345px
        width: 345px
        opacity: .3
        z-index: -9
    &__img
        height: 240px
        width: 240px
        border-radius: 50%
.text-block 
    width: 500px
    max-width: 90%
    &__text 
        font-family: 'Roboto-Regular'
        font-size: 25px
        font-weight: 400
        color: #F6C866
        text-align: center
.text-white
    color: #fff
    position: relative

.text-yellow
    color: #F6C866
    font-weight: 500
.button-block__btn
    margin-top: 34px
    width: 310px
    height: 70px    
    background-image: linear-gradient(45deg, #F09819 0%, #EDDE5D  21%, #FEAD35 40%, #FEAD35  100%)
    outline: none
    border: none
    color: #fff
    font-family: 'Roboto-Regular'
    font-size: 20px
    font-weight: 400
    border-radius: 35px
    &:hover    
        background-image: linear-gradient(45deg, #F09819 0%, #EDDE5D  71%, #FEAD35 100%)
        color: #fff
        text-decoration: none

.detail-text 
    margin-top: 34px
    color: rgba(255,255,255,.6)
    font-size: 16px
    letter-spacing: 1.6px
.hands-img 
    height: 150px
    width: 150px
    border-radius: 50%
    position: relative
    top: -50px
.text-wrap 
    margin-top: 80px
    width: 442px
    height: 442px
    max-width: 90%
    line-height: 35px
    border: 1px solid rgba(255,255,255,.6)
    p
        top: -50px

.meditation
    margin-top: 70px
    height: 606px
    width: 1440px
    max-width: 100%
    background-image: url('../assets/img/meditation.png')   
    background-position: 20%
    background-size: cover
    p
        width: 380px
        max-width: 80%
    @media(max-width: 600px)
        width: 100vw

.dimmer 
    background: rgba(0,0,0,.7)
    height: 100%
    width: 100%
</style>



