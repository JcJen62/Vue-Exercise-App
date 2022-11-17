<template>
  <h1>My Exercise App</h1>
  <NewExercises @add:exercises='addExercise' />
  <h2 class="title">Your Current Exercises</h2>
  <CurrentExercises @edit:exercises='editDate' :exercises="currentExercises"/>
  <h2 class="title">Your Past Exercises</h2>
  <PastExercises :exercises="pastExercises" />
</template>

<script>
import CurrentExercises from './components/CurrentExercises.vue'
import NewExercises from './components/NewExercise.vue'
import PastExercises from './components/PastExercise.vue'

import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'App',
  components: {
    CurrentExercises,
    NewExercises,
    PastExercises
  },
  data() {
    return {
      currentExercises: [
        {
          id: 1,
          name: 'Treadmill',
          notes: '2 miles 30min',
          date: ''
        },
        {
          id: 2,
          name: 'Stair Step',
          notes: '30 Flights 25min',
          date: ''
        },
        {
          id: 3,
          name: 'Bench Press',
          notes: '5X5 145lbs',
          date: ''
        },
        {
          id: 4,
          name: 'Squats',
          notes: '5X4 200lbs',
          date: ''
        },
      ],
      pastExercises: [
        {
          id: 5,
          name: 'Bicep Curls',
          notes: '3X8 30lbs',
          date: '01/02/2022'
        },
        {
          id: 6,
          name: 'Bike',
          notes: '30min 6miles',
          date: '09/10/2021'
        },
        {
          id: 7,
          name: 'Tricep Dips',
          notes: '5X5 40lbs',
          date: '10/24/2021'
        }
      ]
    }
  },
  methods: {
    addExercise(exercises) {
        const id = uuidv4()
        const newExercises = { ...exercises, id}
        
        this.currentExercises = [ ...this.currentExercises, newExercises]
    },
    editDate(id) {
      const newDate = Date.now()
      const strDate = newDate.toString()
      this.currentExercises = this.currentExercises.map(elm => {
        if(elm.id === id){
           elm.date = strDate
          }
        return elm
      })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 60px;
}

body {
  background-color: rgb(116, 143, 153);
}

.title {
  border-bottom: 1px solid white;
  width: 30%;
  margin: 0 auto;
  margin-top: 2rem;
  margin-bottom: 0.5rem;
}
</style>