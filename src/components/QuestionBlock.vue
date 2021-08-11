<template>
    <div class="questions">
        <div class="question-block">
            <p class="question-text">{{ questions[currentQuestion].questionText }}</p>
            <div class="button-block">
                <button v-for="option, index in questions[currentQuestion].options" :key="index" class="button-block__btn">{{ option }}</button>
            
            </div>
            <p class="question-text__num">Вопрос {{ questions[0].number }}- 5  </p>
        </div>

        <div class="question-block">
            <p class="question-text">{{ questions[1].questionText }}</p>
            <div class="button-block">
                <button v-for="option, index in questions[1].options" :key="index" class="button-block__btn">{{ option }}</button>
            </div>
            <p class="question-text__num">Вопрос {{ questions[1].number }}- 5  </p>
        </div>

        <div class="question-block">
            <p class="question-text">{{ questions[2].questionText }}</p>

            <div class="button-block">
                <input class="date-input day" name="day" type='select' />
                <button class="button-block__btn">Далее</button>
            </div>
            <p class="question-text__num">Вопрос {{ questions[1].number }}- 5  </p>
        </div>
    </div>

</template>


<script>


export default {
    name: 'QuestionBlock',

    data(){
        return {
            currentQuestion: 0,
            questions: [
                {number: '1', questionText: 'Боитесь ли вы умереть?', options: ['Да', 'Нет']}, 
                {number: '2', questionText: 'Когда Вы чувствуете себя наиболее комфортно?', options: ['Утро', 'День', 'Вечер', 'Ночь']},
                {number: '3', questionText: 'Укажите свою дату рождения'}
        
            ], 
            userData: [
                {number: '1', answer: ''}
            ]
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
    width: 310px
    height: 70px        
    outline: none
    border: none
    background-color: #fff
    font-family: 'Roboto-Regular'
    font-size: 20px
    font-weight: 400
    border-radius: 35px
</style>