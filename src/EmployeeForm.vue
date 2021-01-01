<template>
  <form @submit.prevent="handleSubmit" id="employee-form">
    <label>Name</label>
    <input v-model="employee.name" type="text" />
    <label>Email</label>
    <input v-model="employee.email" type="text" />
    <button>Add Employee</button>
  </form>
</template>

<script>
export default {
  setup(props, { emit }) {
    const employee = { name: "", email: "" };
    return {
      employee,
      handleSubmit: () => {
        fetch({ method: "POST", url: "/employee/create" }).then(() => {
          console.log("tried to POST employee data");
        });
        emit("add:employee", employee);
      },
    };
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}
</style>