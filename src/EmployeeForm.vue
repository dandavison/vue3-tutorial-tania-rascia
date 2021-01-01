<template>
  <form @submit.prevent="handleSubmit" id="employee-form">
    <label>Name</label>
    <input v-model="employee.name" type="text" />
    <label>Email</label>
    <input v-model="employee.email" type="text" />
    <button>Add Employee</button>
  </form>
  <div v-if="error && submitting" class="error-message">
    ❗Please fill out all required fields
  </div>
  <div v-if="success" class="success-message">
    ✅ Employee successfully added
  </div>
</template>

<script>
import { computed, ref } from "vue";
export default {
  setup(props, { emit }) {
    let employee = { name: "", email: "" };
    let submitting = ref(false);
    let error = ref(false);
    let success = ref(false);

    const invalidName = computed(() => employee.name === "");
    const invalidEmail = computed(() => employee.email === "");

    const clearStatus = () => {
      success.value = false;
      error.value = false;
    };

    const handleSubmit = () => {
      submitting.value = true;
      clearStatus();
      if (employee.name === "" || employee.email == "") {
        // FIXME: use computed properties
        error.value = true;
        return;
      }

      fetch({ method: "POST", url: "/employee/create" }).then(() => {
        console.log("tried to POST employee data");
        emit("add:employee", employee);
        employee = { name: "", email: "" };
        error.value = false;
        submitting.value = false;
        success.value = true;
      });
    };

    return {
      employee,
      handleSubmit,
      submitting,
      error,
      success,
    };
  },
  emits: ["add:employee"],
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}

[class*="-message"] {
  font-weight: 500;
}

.error-message {
  color: #d33c40;
}

.success-message {
  color: #32a95d;
}
</style>