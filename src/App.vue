<template>
  <h1>Welcome to Your Courses</h1>
  <p>Number of courses selected: {{ count }}</p>
  <div class="container">
    <div class="course-grid">
      <CourseItem
        v-for="course of courses"
        :key="course.id"
        :course="course"
        @count-student="countSelection"
        @remove-student="removeSelection"
      />
    </div>
  </div>
</template>

<script>
import CourseItem from "./components/CourseItem.vue";

export default {
  name: "App",
  data() {
    return {
      count: 0,
      courses: [
        {
          id: 1,
          name: "Vue.js",
          credits: 3,
          hours: 40,
          students: 20,
          location: "Vanier",
          description: "A lot of mind-bending stuff. Brain hurting.",
        },
        {
          id: 2,
          name: "Frameworks",
          credits: 3,
          hours: 40,
          students: 19,
          location: "Vanier",
          description: "Even more stuff.",
        },
        {
          id: 3,
          name: "Programming",
          credits: 3,
          hours: 40,
          students: 15,
          location: "Vanier",
          description: "Even more hurt.",
        },
        {
          id: 4,
          name: "Design",
          credits: 3,
          hours: 60,
          students: 12,
          location: "Vanier",
          description: "Designing stuff.",
        },
        {
          id: 5,
          name: "Writing",
          credits: 3,
          hours: 50,
          students: 22,
          location: "Vanier",
          description: "Writing stuff.",
        },
        {
          id: 6,
          name: "Advanced Programming",
          credits: 3,
          hours: 40,
          students: 15,
          location: "Vanier",
          description: "Even more hurt multiplied by 10.",
        },
      ],
    };
  },
  components: {
    CourseItem,
  },
  methods: {
    countSelection() {
      this.count++;
    },
    removeSelection() {
      this.count--;
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  width: 90%;
  max-width: 1200px;
  margin: auto;
}

.course-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;
}
</style>
