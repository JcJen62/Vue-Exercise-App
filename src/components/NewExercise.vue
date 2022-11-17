<template>
  <div id="formContainer">
    <form @submit.prevent="handleSubmit">
      <input
        v-model="exercises.name"
        type="text"
        placeholder="Name of Exercise"
      />
      <input
        v-model="exercises.notes"
        type="text"
        placeholder="Notes for Exercise"
      />
      <button type="submit" id="addBtn">Add Exercise</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "formContainer",
  data() {
    return {
      exercises: {
        name: "",
        notes: "",
      },
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("add:exercises", this.exercises);
      this.exercises = {
        name: "",
        notes: "",
      };
    },
  },
};
</script>

<style scoped>
#formContainer input {
  margin: 0.5rem;
  padding: 6px;
}

#addBtn {
  padding: 8px;
  border-radius: 5px;
  border: none;
  cursor: pointer;
}
</style>