<template>
  <div v-if="course.students < 20" class="course" :class="{ added: button }">
    <h2>{{ course.name }}</h2>
    <div class="course-info">
      <p>
        Id: {{ course.id }}, Credits: {{ course.credits }}, Hours:
        {{ course.hours }}, Location: {{ course.location }}
      </p>
      <p>{{ course.description }}</p>
      <p>Students: {{ course.students }}/20</p>
    </div>
    <button
      :id="course.id"
      v-if="course.students < 20 && button == 0"
      @click="addStudent"
    >
      Add Course
    </button>
    <button
      v-else-if="course.students < 20"
      :class="{ removeButton: button }"
      @click="removeStudent"
    >
      Remove Course
    </button>
  </div>
  <div v-if="course.students >= 20" class="full">
    <h2>{{ course.name }}</h2>
    <div class="course-info">
      <p>
        Id: {{ course.id }}, Credits: {{ course.credits }}, Hours:
        {{ course.hours }}, Location: {{ course.location }}
      </p>
      <p>{{ course.description }}</p>
      <p>Students: {{ course.students }}/20</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CourseItem",
  data() {
    return {
      button: 0,
    };
  },
  props: {
    course: {
      type: Object,
      required: true,
    },
  },
  methods: {
    addStudent() {
      this.$emit("count-student");
      this.button = 1;
    },
    removeStudent() {
      this.$emit("remove-student");
      this.button = 0;
    },
  },
};
</script>

<style scoped lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

h2 {
  margin-bottom: 2rem;
}

p {
  margin-bottom: 1rem;
}

button {
  padding: 10px 25px;
  background-color: #4683b4a1;
  border: none;
  border-radius: 10px;
}

.course {
  padding: 30px;
  border: 1px solid #4682b4;
  border-radius: 10px;
}

.course-info {
  text-align: left;
}

.full {
  padding: 30px;
  background-color: rgba(241, 84, 84, 0.7);
  border: 1px solid #4683b4;
  border-radius: 10px;
}

.added {
  background-color: rgba(70, 182, 70, 0.7);
}

.removeButton {
  background-color: aliceblue;
}
</style>
