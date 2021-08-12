<template>
    <div class="questions">
        <div class="question-block">
            <p class="question-text">{{ questions[0].questionText }}</p>
            <div class="control-block">
                <button v-for="option, index in questions[0].options" :key="index" class="btn btn-yellow">{{ option }}</button>            
            </div>
            <p class="question-text__num">Вопрос 1-5  </p>
        </div>

        <RunicMsg :messageText="`${runicMessages[0]}`" />

        <div class="question-block">
            <p class="question-text">{{ questions[1].questionText }}</p>
            <div class="control-block">
                <button v-for="option, index in questions[1].options" :key="index" class="btn btn-yellow">{{ option }}</button>
            </div>
            <p class="question-text__num">Вопрос 2-5  </p>
        </div>

        <RunicMsg :messageText="`${runicMessages[1]}`" />

        <div class="question-block">
            <p class="question-text">{{ questions[2].questionText }}</p>

            <div class="control-block">
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

                <button class="btn btn-yellow" @click="applyDate">Далее</button>
            </div>
            <p class="question-text__num">Вопрос 3-5  </p>

            <Spinner v-if="this.loading" />
            <Message v-if="this.showMessage" :text="`${afterAgeMsg[userAgeCategory]}`" />


            <div class="question-block">
                <p class="question-text">{{ questions[3].questionText }}</p>
                <div class="control-block">
                    <button v-for="option, index in questions[3].options" :key="index" class="btn btn-yellow">{{ option }}</button>
                </div>
                <p class="question-text__num">Вопрос 4-5  </p>
            </div>

            <div class="question-block">
                <p class="question-text">{{ questions[4].questionText }}</p>
                <div class="control-block">
                    <button class="btn btn-yellow" @click="testComplete">Да</button>
                    <button class="btn btn-yellow">Затрудняюсь ответить</button>
                </div>
                <p class="question-text__num">Вопрос 5-5  </p>
            </div>


            <MicLoader v-if="this.isCompleted" />
            <ResultBlock v-if="this.showResult" />
        </div>
    </div>

</template>


<script>
import RunicMsg from './RunicMsg.vue'
import Spinner from './Spinner.vue'
import Message from './Message.vue'
import MicLoader from './MicLoader.vue'
import ResultBlock from './ResultBlock.vue'
export default {
    name: 'QuestionBlock',
    components: {
        RunicMsg,
        Spinner,
        Message,
        MicLoader,
        ResultBlock
    },

    data(){
        return {            
            months: ['Январь', 'Февраль','Март','Апрель','Май','Июнь','Июль','Август','Сентябрь','Октябрь', 'Ноябрь', 'Декабрь'],
            questions: [
                {questionText: 'Боитесь ли вы умереть?', options: ['Да', 'Нет']}, 
                {questionText: 'Когда Вы чувствуете себя наиболее комфортно?', options: ['Утро', 'День', 'Вечер', 'Ночь']},
                {questionText: 'Укажите свою дату рождения'},
                {questionText: 'Снятся ли Вам умершие люди?', options: ['Да', 'Нет', 'Иногда']},
                {questionText: 'Запись, которую Вы услышите, может шокировать людей с неокрепшей психикой. Вы готовы узнать, что ждет именно Вас?'}
        
            ], 
            userData: {
                birthday: '',
                birthmonth: '',
                birthyear: ''
            },
            isCompleted: false,
            showResult: false,
            afterAgeMsg: ['По вам скучает очень близкий человек, которого больше нет в мире живых.',
                        'По вам скучает очень близкий человек, которого больше нет в мире живых. Возможно это дедушка или бабушка.',
                        'По вам скучает очень близкий человек, которого больше нет в мире живых. Возможно это кто-то из Ваших родителей.'
            ],
            runicMessages: [
                'Вы, конечно, умрете. И все, с кем вы знакомы, тоже однажды умрут.', 'Мы расскажем Вам не только подробности вашей смерти, но также поможем Вам избежать этой ужасной даты и продлить вашу жизнь на многие годы.'
            ],
            loading: false,
            showMessage: false
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
            if (this.userData.birthday == ''){
                document.getElementById("day").classList.add('error-select')
            }
            if (this.userData.birthmonth == ''){
                document.getElementById("month").classList.add('error-select')
            }
            if (this.userData.birthyear == ''){
                document.getElementById("year").classList.add('error-select')
            }
            else {
                this.loading = true
                setTimeout(()=> this.loading = false, 2000);
                let userAge = 2021-parseInt(this.userData.birthyear)
                console.log(userAge)
                if (18 < userAge <= 35){
                    this.userAgeCategory = 0
                }
                if (36 <= userAge <=45){
                    this.userAgeCategory = 1
                }
                if (userAge >= 45){
                    this.userAgeCategory = 2
                }
                console.log(this.userAgeCategory)
                setTimeout(()=> this.showMessage = true, 2000);
            }
        },  
        testComplete(){
            this.isCompleted = true
            setTimeout(()=> this.isCompleted = false, 3000)
            setTimeout(()=> this.showResult = true, 3000);
        }   
    }
}
</script>


<style lang="sass" scoped>
.question-block
    margin-top: 100px
    display: flex
    flex-direction: column
    align-items: center
    justify-content: center
.question-text 
    color: #F6C866
    width: 500px
    max-width: 80%
    text-transform: uppercase
    text-align: center
    font-size: 25px
    line-height: 35px
    font-family: 'Roboto-Regular'
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
.error-select
    border: 2px solid red

</style>