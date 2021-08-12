<template>
    <div class="questions">
        <div class="question-block">
            <p class="question-text">{{ questions[0].questionText }}</p>
            <div class="button-block">
                <button v-for="option, index in questions[0].options" :key="index" class="button-block__btn">{{ option }}</button>
            
            </div>
            <p class="question-text__num">Вопрос 1-5  </p>
        </div>


        <RunicMsg :messageText="`${runicMessages[0]}`" />

        <div class="question-block">
            <p class="question-text">{{ questions[1].questionText }}</p>
            <div class="button-block">
                <button v-for="option, index in questions[1].options" :key="index" class="button-block__btn">{{ option }}</button>
            </div>
            <p class="question-text__num">Вопрос 2-5  </p>
        </div>

        <div class="question-block">
            <p class="question-text">{{ questions[2].questionText }}</p>

            <div class="button-block">
                <select required class="date-input" id="day" name="day" v-model="userData.birthday">
                    <option class="date-option" disabled value="">День</option>
                    <option class="date-option" v-for="index in 31" :key="index" :value="`${index}`">{{index}}</option>
                </select>

                <select required class="date-input" id="month" name="month" v-model="userData.birthmonth">
                    <option class="date-option" disabled value="">Месяц</option>
                    <option class="date-option" v-for="month, index in months" :key="index" :value="`${month}`">{{month}}</option>
                </select>

                
                <select required class="date-input" id="year" name="year" v-model="userData.birthyear">
                    <option class="date-option" disabled value="">Год</option>
                    <option v-for="year in years" :key="year" :value="year">{{ year }}</option>
                </select>

                <button class="button-block__btn" @click="applyDate">Далее</button>
            </div>
            <p class="question-text__num">Вопрос 3-5  </p>
        </div>
    </div>

</template>


<script>
import RunicMsg from './RunicMsg.vue'
export default {
    name: 'QuestionBlock',
    components: {
        RunicMsg
    },

    data(){
        return {            
            months: ['Январь', 'Февраль','Март','Апрель','Май','Июнь','Июль','Август','Сентябрь','Октябрь', 'Ноябрь', 'Декабрь'],
            questions: [
                {number: '1', questionText: 'Боитесь ли вы умереть?', options: ['Да', 'Нет']}, 
                {number: '2', questionText: 'Когда Вы чувствуете себя наиболее комфортно?', options: ['Утро', 'День', 'Вечер', 'Ночь']},
                {number: '3', questionText: 'Укажите свою дату рождения'}
        
            ], 
            userData: {
                birthday: '',
                birthmonth: '',
                birthyear: ''

            },
            runicMessages: [
                'Вы, конечно, умрете. И все, с кем вы знакомы, тоже однажды умрут.', 'sdfskjdfhskjdfhkjdfhskjdfh'
            ]
        }
    },
    computed: {
        years () {
            let years = []
            for (let i=1930; i<2021; i++){
                years.push(i)
            }
            return years
        }

    },
    methods: {
        applyDate(){
            console.log(this.userData.birthday)
        }
    }
}
</script>


<style lang="sass" scoped>
.question-block
    margin-top: 100px
.question-text 
    color: #F6C866
    text-transform: uppercase
    text-align: center
    &__num 
        text-align: center
        color: rgba(255,255,255,.6)
.date-input 
    margin-top: 20px
    width: 310px
    height: 70px        
    outline: none
    border: none    
    text-align: center
    border-radius: 35px
    font-size: 20px
    text-align-last: center
    -webkit-appearance: none
    appearance: none     
    line-height: 1
    background-image: url('../assets/img/dropdown.svg')
    background-repeat: no-repeat
    background-size: 20px 25%
    background-position: right 20px center, right bottom, right bottom, right bottom 
    background-color: #E5E5E5
    color: #000

option
    color: #000
option:first-child
    color: #000

</style>