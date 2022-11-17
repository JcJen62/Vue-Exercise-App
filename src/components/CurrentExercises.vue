<template>
  <div id="containerCurrent">
    <n-card v-for="exercise in exercises" :key="exercise.id" hoverable>
      <h2>{{ exercise.name }}</h2>
      {{ exercise.notes }}
      <p>{{ exercise.date }}</p><br />
      <button @click="handleDate(exercise)" id="dateBtn">Add Completed Date</button>
    </n-card>
  </div>
</template>

<script>
import { NCard } from "naive-ui";

export default {
  name: "currentExercises",
  props: {
    exercises: Array,
  },
  data() {
    return {
      
    };
  },
  components: {
    NCard,
  },
  methods: {
      handleDate(exercise){
          this.$emit('edit:exercises', exercise.id)
      }
  }
};
</script>

<style scoped>
.n-card {
  max-width: 300px;
  border: solid 1px rgb(51, 51, 51);
  margin: 1rem;
}

#containerCurrent {
  justify-content: center;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

#dateBtn {
  padding: 8px;
  border-radius: 5px;
  border: none;
  cursor: pointer;
  background-color: rgb(193, 227, 231);
  margin-top: 0.3rem;
}
</style>