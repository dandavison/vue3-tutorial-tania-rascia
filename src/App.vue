<template>
  <div id="app-component"></div>
  <h1>Employees</h1>
  <employee-table v-bind:employees="employees" />
</template>

<script>
import EmployeeTable from "./EmployeeTable.vue";
export default {
  setup() {
    return {
      employees: [
        { name: "Richard Hendricks", email: "richard@piedpiper.com", id: 1 },
        { name: "Bertram Gilfoyle", email: "gilfoyle@piedpiper.com", id: 2 },
        { name: "Dinesh Chugtai", email: "dinesh@piedpiper.com", id: 3 },
      ],
    };
  },
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
