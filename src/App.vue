<template>
    <div id="app">
        <h1>Super Quiz</h1>     
        <transition name="flip" mode="out-in">
            <question v-if="questionMode"
                :question="questions[currentQuestion]"
                @answered="showResult"></question>
            <result v-else
                :result="result"
                @confirmed="nextQuestion"/>
        </transition>   
    </div>
</template>

<script>
import questions from '@/util/questions'
import Question from '@/components/Question.vue'
import Result from '@/components/Result.vue'

export default {
    name: "app",
    components: { Question, Result},
    data(){
        return{
            result : false,
            questionMode: true,
            questions: questions,
            currentQuestion: 0,
        }
    },
    methods:{
        showResult(result){
            this.result = result;
            this.questionMode = false;
        },
        nextQuestion(){
            let r = Math.random() * this.questions.length;
            this.currentQuestion = parseInt(r);
            this.questionMode = true;
        }
    }    
};
</script>

<style>
body {
    background-image: linear-gradient(
    to right top,
    #0f3b7e,
    #29589b,
    #4277b9,
    #5a96d7,
    #75b7f4
    );
    font-family: 'Oswald', sans-serif;
    color: #ffffff;
    height: 100vh;
    
}
#app {    
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;

    flex-direction: column;
    align-items: center;
}

#app h1{
    font-weight: 200;
    font-size: 4rem;
}

@keyframes flip-out {
    from {transform: rotateY(0deg)}
    to {transform: rotateY(90deg)}
}

@keyframes flip-in {
    from {transform: rotateY(90deg)}
    to {transform: rotateY(0deg)}
}

.flip-enter-active{
    animation: flip-in 0.3s ease;
}

.flip-leave-active{
    animation: flip-out 0.3s ease;
}

</style>
