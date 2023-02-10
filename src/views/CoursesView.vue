<template>
  <h3>All Subjects</h3>
  <hr />
  <table>
    <tr>
      <th>Subject code</th>
      <th>Subject name</th>
    </tr>

    <tr v-for="(course, index) in courses" :key="index">
      <td style="text-align: left; padding: 10px; border: 1px solid #ddd;">{{ course.course_id }}</td>
      <td style="text-align: left; padding: 10px; border: 1px solid #ddd;">
        {{ course.course_name }}
      </td>
    </tr>
  </table>
</template>

<script>
  import courses from "../json/cs_courses.json";

  export default {
    data() {
      return {
        courses: courses
      };
    }
  };
</script>

<style>
  table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
  }

  th {
    background-color: #333;
    color: #fff;
    font-weight: bold;
    padding: 10px;
  }

  td {
    border: 1px solid #ddd;
    padding: 10px;
  }
</style>