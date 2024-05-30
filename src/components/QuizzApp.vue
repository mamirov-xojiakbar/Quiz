<template>
  <div>

    <div :class="isSideMenu ? 'w-[calc(100%-45%)]' : 'w-[calc(100%-65px)]'" class="shadow-md duration-300">
      <h1 class="py-8 text-3xl text-center ">Matematika</h1>



    </div>

    <div class="m-10 duration-300" :class="isSideMenu ? 'w-[calc(100%-50%)] ' : 'w-[1000px] mx-auto '">
      <QuizzItem v-for="quizz, index in quizzes" :quizz="quizz" @user-select-answer="handleSelectAnswer" />



    </div>

    <div :class="isSideMenu ? 'w-[calc(100%-45%)]' : 'w-[calc(100%-65px)]'"
      class="bg-black duration-300 p-24 flex flex-col items-center">

      <div v-if="isFinishTest" class="text-white relative">
        <div class="absolute text-[13px] top-14 left-6">
          <p>To'g'ri javoblar soni : {{ trueQuizzes }}</p>
          <p>Umumiy foiz : {{ percentQuizzes }} %</p>
          <p>Umumiy ball : {{ userBall }} / 100 </p>
        </div>

        <circle-progress :percent="percentQuizzes" />
      </div>


      <button @click="finishTest" class=" py-3 px-5 rounded bg-primary w-[200px] mt-5">
        {{ isFinishTest ? 'Qayta topshirish' : 'Testni yakunlash' }} </button>
    </div>


    <QuizzSider v-model="isSideMenu" />


  </div>
</template>

<script setup>
import "vue3-circle-progress/dist/circle-progress.css";
import CircleProgress from "vue3-circle-progress";
import { ref, reactive } from 'vue';
import QuizzSider from './QuizzSider.vue';
import QuizzItem from './QuizzItem.vue';

const isSideMenu = ref(false)

const quizzes = reactive([
  {
    id: 1,
    question: '2+2 = ?',
    answers: ['4', '2', '3', '5'],
    correctAnswer: '4',
  },
  {
    id: 2,
    question: '2+12 = ?',
    answers: ['4', '2', '3', '5'],
    correctAnswer: '4',
  },
  {
    id: 3,
    question: '2+6 = ?',
    answers: ['4', '2', '3', '5'],
    correctAnswer: '4',
  },
  {
    id: 4,
    question: '5+2 = ?',
    answers: ['4', '2', '3', '5'],
    correctAnswer: '4',
  },
  {
    id: 5,
    question: '1+2 = ?',
    answers: ['4', '2', '3', '5'],
    correctAnswer: '4',
  },
])


const handleSelectAnswer = (obj) => {

  quizzes.forEach((item) => {
    if (item.id == obj.id) {
      item.userAnswer = obj.userAnswer
    }
  })


}

const isFinishTest = ref(false)
const trueQuizzes = ref(0)
const percentQuizzes = ref(0)
const userBall = ref(0)

const finishTest = () => {
  isFinishTest.value = true
  quizzes.forEach((item) => {
    if (item.correctAnswer == item.userAnswer) {
      trueQuizzes.value++
    }
  })

  percentQuizzes.value = trueQuizzes.value * 100 / quizzes.length
  userBall.value = percentQuizzes.value
}


</script>

<style lang="scss" scoped></style>