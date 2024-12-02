<template>
  <form @submit.prevent="onSubmit">
    <h2 class="label-wrapper">
      <label for="course-select" class="label__lg">4 courses available</label>
    </h2>
    <select id="course-select" v-model="selectedCourse" class="input__lg">
      <option value="" disabled>Select a course</option>
      <option v-for="course in predefinedCourses" :key="course" :value="course">
        {{ course }}
      </option>
    </select>
    <button type="submit" class="btn btn__primary btn__lg" :disabled="!selectedCourse">
      Add Course
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      predefinedCourses: [
        "CNIT 103 - Hardware",
        "CNIT 131 – Internet & Intro to HTML, CSS",
        "CNIT 106 – Introduction to Networks",
        "CNIT 120 – Network Security",
      ],
      selectedCourse: "", // The currently selected course
    };
  },
  methods: {
    onSubmit() {
      if (!this.selectedCourse) return;
      this.$emit("course-added", this.selectedCourse); // Emit the selected course to the parent
      this.selectedCourse = ""; // Reset the dropdown
    },
  },
};
</script>

<style scoped>
.label-wrapper {
  margin-bottom: 10px;
}
.input__lg {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  margin-bottom: 10px;
}
.btn__primary {
  background-color: #007bff;
  color: black;
  border: none;
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
}
</style>
