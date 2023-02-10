<template>
  <div>
    <h4>Search</h4>
    <form @submit.prevent="addToBasket">
      <input type="text" v-model="courseID" placeholder="Subject code" />
      <button type="submit">register</button>
    </form>

    <article v-if="(x = courseData.find((elem) => elem.course_id == courseID))">
      <div class="border">
        <p>
          <b>Subject code : </b> <span>{{ x.course_id }}</span>
        </p>
        <p>
          <b>Subject name : </b> <span>{{ x.course_name }}</span>
        </p>
        <p>
          <b>credit : </b><span>{{ x.credit }}</span>
        </p>
      </div>
    </article>
    <article v-else>
      <p>not found</p>
    </article>

    <hr />
    <div>
      <h4>waiting for submit</h4>
      <table>
        <thead>
          <th>Subject code</th>
          <th>Subject name</th>
          <th>credit</th>
        </thead>
        <tbody>
          <tr v-for="(course, index) in courseInfo" :key="index">
            <td>{{ course.course_id }}</td>
            <td>{{ course.course_name }}</td>
            <td>{{ course.credit }}</td>
            <td><button @click="removeFromBasket(index)">ลบ</button></td>
          </tr>
        </tbody>
      </table>
      <button @click="enrollCourse">submit</button>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import courseData from "../json/cs_courses.json";
import { useEnrollment } from "../stores/useEnrollment";

const enrollment = useEnrollment();

const courseID = ref("");
let courseInfo = ref([]);
function addToBasket() {
  const data = courseData.find((elem) => elem.course_id == courseID.value);
  //console.log(data);
  if (data) {
    courseInfo.value.push(data);
    courseID.value = "";
  } else {
    alert("Pls enter your subject code");
  }
}
function removeFromBasket(course_key) {
  if (confirm("delete subject ?")) {
    courseInfo.value.pop(course_key);
  }
}
function enrollCourse() {
  if (courseInfo.value.length != 0) {
    courseInfo.value.forEach((subject) => {
      enrollment.storeState(subject);
    });
    console.log(enrollment.getState);
    courseInfo.value = [];
    alert("already submit");
  } else {
    alert("chose subject");
  }
}
</script>
<style scoped>
.border {
  margin: 20px auto;
  padding: 0.5em;
  border: 3px solid gray;
  border-radius: 10px;
}

form {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px 0;
}

input[type="text"] {
  width: 50%;
  padding: 0.5em;
  border-radius: 10px;
  border: none;
  outline: none;
}

button[type="submit"] {
  padding: 0.5em 1em;
  background-color: green;
  color: white;
  border-radius: 10px;
  border: none;
  outline: none;
  cursor: pointer;
  margin-left: 1em;
}

table {
  width: 100%;
  border-collapse: collapse;
}

thead {
  background-color: lightgray;
}

th,
td {
  padding: 0.5em;
  text-align: left;
}

tbody tr:nth-child(even) {
  background-color: lightgray;
}

button {
  padding: 0.5em 1em;
  background-color: red;
  color: white;
  border-radius: 10px;
  border: none;
  outline: none;
  cursor: pointer;
  margin-left: 1em;
}
</style>

