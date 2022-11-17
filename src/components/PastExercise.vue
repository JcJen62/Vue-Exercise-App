<template>
  <div id="containerPast">
    <n-card
      v-for="exercise in exercises"
      :key="exercise.id"
      hoverable
      >
      <h2>{{exercise.name}}</h2>
      {{ exercise.notes }}
      <p>{{exercise.date}}</p>
      </n-card>
  </div>
</template>

<script>
import { NCard } from "naive-ui";

export default {
  name: "pastExercises",
  props: {
    exercises: Array,
  },
  data() {
    return {
      editing: null,
    };
  },
  components: {
    NCard,
  },
};
</script>

<style scoped>
.n-card {
  max-width: 300px;
  border: solid 1px rgb(51, 51, 51);
  margin: 1rem;
}

#containerPast {
  justify-content: center;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>