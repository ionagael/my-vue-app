<template>
  <div>
    <h1>Study Plan</h1>
    <course-form @course-added="addCourse"></course-form>
    <h2 id="list-summary">{{ courseSummary }}</h2>
    <ul aria-labelledby="list-summary" class="stack-large">
      <li v-for="course in courses" :key="course.id">
        <course-item
          :id="course.id"
          :title="course.title"
          :completed="course.completed"
          @course-completed="markAsCompleted(course.id)"
          @course-deleted="deleteCourse(course.id)"
        ></course-item>
      </li>
    </ul>
  </div>
</template>

<script>
import { nanoid } from "nanoid";
import CourseForm from "./components/CourseForm.vue";
import CourseItem from "./components/CourseItem.vue";

export default {
  name: "App",
  components: {
    CourseForm,
    CourseItem,
  },
  data() {
    return {
      courses: [
        { id: "course-" + nanoid(), title: "CNIT 103 - Hardware", completed: false },
        { id: "course-" + nanoid(), title: "CNIT 131 - Internet & Intro to HTML, CSS", completed: false },
        { id: "course-" + nanoid(), title: "CNIT 106 - Introduction to Networks", completed: false },
        { id: "course-" + nanoid(), title: "CNIT 120 - Network Security", completed: false },
      ],
    };
  },
  computed: {
    courseSummary() {
      return `${this.courses.length} courses listed`;
    },
  },
  methods: {
    addCourse(newCourseTitle) {
      this.courses.push({ id: "course-" + nanoid(), title: newCourseTitle, completed: false });
    },
    deleteCourse(courseId) {
      this.courses = this.courses.filter((course) => course.id !== courseId);
    },
    markAsCompleted(courseId) {
      const course = this.courses.find((course) => course.id === courseId);
      if (course) {
        course.completed = !course.completed;
      }
    },
  },
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #f9f9f9;
  margin: 0;
  padding: 0 20px;
}
.stack-large {
  margin: 20px 0;
  padding: 0;
  list-style: none;
}
h1 {
  color: black;
}
h2 {
  color: black;
}
</style>
