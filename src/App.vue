<template>
  <div id="app-component" class="small-container">
    <employee-form @add:employee="addEmployee" />
    <h1>Employees</h1>
    <employee-table v-bind:employees="employees" />
  </div>
</template>

<script>
import { ref } from "vue";
import EmployeeForm from "./EmployeeForm.vue";
import EmployeeTable from "./EmployeeTable.vue";
export default {
  setup() {
    const employees = ref([
      { name: "Richard Hendricks", email: "richard@piedpiper.com", id: 1 },
      { name: "Bertram Gilfoyle", email: "gilfoyle@piedpiper.com", id: 2 },
      { name: "Dinesh Chugtai", email: "dinesh@piedpiper.com", id: 3 },
    ]);
    const addEmployee = (employee) => {
      console.log(`addEmployee: ${employee.name} ${employee.email}`);
      const nextId = employees.value.length + 1;
      employees.value.push({ ...employee, nextId });
    };
    return {
      employees,
      addEmployee,
    };
  },
  components: { EmployeeTable, EmployeeForm },
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
