<template>
    <div class="result-block">
        <div class="bubble-block">
            <div class="bubble bubble-bottom-left"><p class="result-block__text">Спасибо за Ваши ответы!<b> Мы подготовили для Вас персональную аудиозапись с Вашим прогнозом.</b></p></div>
            
        </div>
        <p class="result-text">Вы можете узнать, как повлиять на события, которые ожидают вас в ближайшем будущем.</p>
        <div class="danger">
            <p class="danger__text"><b>Первое значимое событие может произойти уже {{ date }},</b> Вам надо быть готовым, чтобы последствия не оказались необратимыми.</p>
        </div>
        <p class="result-text">Нажмите на кнопку ниже прямо сейчас и наберите наш номер телефона. Прослушайте важную информацию!</p>
        <button class="btn btn-green" @click="getResponse">Позвонить и прослушать</button>
        <div class="popup" v-if="this.showResponse">
            <h4>Результат</h4>
            <p>{{response.name}}</p>
            <p>{{response.height}} см, {{response.mass}} кг</p>
            <p></p>
        </div>
    </div>
</template>

<style lang="sass">
.result-block
    dislay: flex
    flex-direction: column 
    justify-content: center
    width: 422px
    max-width: 80%
    font-family: 'Roboto'
    text-align: center
.result-text
    margin: 40px auto   
    color: #fff
    font-size: 14px
    line-height: 16px    
.danger 
    padding: 30px
    font-size: 25px
    color: #F6C866
    border: 1px solid #fff

.popup
    display: flex
    flex-direction: column
    background: #fff
    margin: 30px auto
    height: 200px
    width: 300px
    border-radius: 20px    
</style>

<script>
export default{
    computed: {
        date(){
            let currentDate = new Date(new Date().getTime() + 24 * 60 * 60 * 1000);
            let day = currentDate.getDate()
            let month = currentDate.getMonth() + 1
            let year = currentDate.getFullYear()
            return (day + "." + month + "." + year)
        }                
    },
    data(){
        return {
            showResponse: false,
            // response: []
        }
    },
    methods: {
        async getResponse(){
            this.response = await fetch('https://swapi.dev/api/people/1/').then(res => res.json())
            console.log(this.response.name)
            this.showResponse = true
        }
    }
}
</script>
