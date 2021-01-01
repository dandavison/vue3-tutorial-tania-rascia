<template>
  <div id="app-component"></div>
  <h1>Employees</h1>
  <employee-table />
</template>

<script>
import EmployeeTable from "./EmployeeTable.vue";
export default {
  components: { EmployeeTable },
};
</script>

<style>
EmployeeTable button {
  background: #009435;
  border: 1px solid #009435;
}

.small-container {
  max-width: 680px;
}
</style>
