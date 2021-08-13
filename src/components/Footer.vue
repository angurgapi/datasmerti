<template>
    <div class="footer">
        <p class="footer__text">
            TERMENI SI CONDITII: ACESTA ESTE UN SERVICIU DE</p>
        <p class="footer__text">DIVERTISMENT. PRIN FOLOSIREA LUI DECLARATI CA AVETI</p>
        <p class="footer__text text-hidden"> 18 ANI IMPLINITI,</p>
        
    </div>
</template>

<style lang="sass">
.footer 
    height: 40px
    margin-top: 50px
    display: flex
    flex-direction: column
    justify-content: center
    align-items: center
    &:hover .text-hidden
        display: block

    &__text 
        margin: 0
        text-align: center
        color: #9D9D9D
        font-size: 12px
        letter-spacing: 3px 
        line-height: 18px
        width: 500px
        max-width: 95%       
.text-hidden 
    display: none

</style>