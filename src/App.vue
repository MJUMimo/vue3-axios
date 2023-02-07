<script setup>
import axios from "axios";
import { ref } from "vue";

const data = ref();
const config = {
  method: "get",
  url: "https://api.fda.gov/drug/event.json?limit=10",
  headers: {},
};

axios(config)
  .then(function (response) {
    data.value = response.data.results;
    console.log(data.value);
  })
  .catch(function (error) {
    console.log(error);
  });
</script>
<template>
  <h1>OpenFDA Api</h1>
  <table class="table-bg">
    <thead>
      <th>safetyreportid</th>
      <th>drug</th>
    </thead>
    <tbody>
      <tr v-for="(value, index) in data" :key="index">
        <td>{{ value.safetyreportid }}</td>
        <td>{{ value.companynumb }}</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
.table-bg{
  background: lightblue;
  padding: 10px
}
</style>
