<template>
  <div class="course-grid">
    <div class="course" v-for="course of courses" :key="course.id">
      <h2>{{ course.name }}</h2>
      <p>
        Id: {{ course.id }}, Credits: {{ course.credits }}, Hours:
        {{ course.hours }}, Location: {{ course.location }}
      </p>
      <p>{{ course.description }}</p>
    </div>
    <button @click="increment">Add Course</button>
  </div>
</template>

<script>
export default {
  name: "CourseItem",
  data() {
    return {
      count: 0,
      courses: [
        {
          id: 1,
          name: "Vue.js",
          credits: 3,
          hours: 40,
          location: "Vanier",
          description: "A lot of mind-bending stuff. Brain hurting.",
        },
      ],
    };
  },
  methods: {
    increment() {
      this.$emit("count-student");
    },
  },
};
</script>

<style></style>
