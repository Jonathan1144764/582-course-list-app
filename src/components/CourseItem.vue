<template>
  <div class="course-grid">
    <div class="course" v-for="course of courses" :key="course.id">
      <h2>{{ course.name }}</h2>
      <div class="course-info">
        <p>
          Id: {{ course.id }}, Credits: {{ course.credits }}, Hours:
          {{ course.hours }}, Location: {{ course.location }}
        </p>
        <p>{{ course.description }}</p>
        <p>Students: {{ course.students }}/20</p>
      </div>
      <button :id="course.id" v-if="course.students < 20" @click="addStudent">
        Add Course
      </button>
      <button v-else class="disabled"></button>
    </div>
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
      ],
    };
  },
  methods: {
    increment() {
      this.$emit("count-student");
    },
    addStudent() {
      for (this.course of this.courses) {
        if (this.course.id == event.target.id) {
          this.course.students++;
          event.target.textContent = "Remove course";
        }
      }
    },
  },
};
</script>

<style scoped lang="scss">
.course-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;
}

.course {
  border: 1px solid #4682b4;
  border-radius: 10px;
}

.disabled {
  display: none;
}

.shown {
  display: block;
}
</style>
