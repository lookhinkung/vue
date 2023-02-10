<template>
  <div class="container">
    <h3 class="text-center">My Enrolled Subjects</h3>
    <table class="table table-bordered table-striped">
      <thead>
        <th>Subject code</th>
        <th>Subject name</th>
      </thead>
      <tbody>
        <tr v-for="(subject, index) in myEnrollment" :key="index">
          <td>{{ subject.course_id }}</td>
          <td>{{ subject.course_name }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script setup>
import { useEnrollment } from "../stores/useEnrollment";

const enrollmentList = useEnrollment();

const myEnrollment = enrollmentList.getState;
</script>
<style scoped>
.container {
  padding: 20px;
}

.text-center {
  text-align: center;
}
</style>