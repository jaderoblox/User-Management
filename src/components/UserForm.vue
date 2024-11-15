<template>
  <h4 class="text-center mb-4 text-primary"></h4>
  <form @submit.prevent="handleSubmit">
    <div class="mb-3">
      <label for="name" class="form-label">
        <i class="bi bi-person me-1"></i>Name
      </label>
      <input
        v-model="name"
        id="name"
        type="text"
        class="form-control custom-input"
        placeholder="Enter your name"
        required
      />
    </div>
    <div class="mb-3">
      <label for="email" class="form-label">
        <i class="bi bi-envelope me-1"></i>Email
      </label>
      <input
        v-model="email"
        id="email"
        type="email"
        class="form-control custom-input"
        placeholder="Enter your email"
        required
      />
    </div>
    <div class="mb-3">
      <label for="phone" class="form-label">
        <i class="bi bi-telephone me-1"></i>Contact Number
      </label>
      <input
        v-model="phone"
        id="phone"
        type="tel"
        class="form-control custom-input"
        placeholder="Enter your contact number"
        required
      />
    </div>
    <div class="d-flex justify-content-end">
      <button type="submit" class="btn custom-button btn-lg">
        <i class="bi bi-plus-circle me-1"></i>Add User
      </button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      phone: "",
    };
  },
  methods: {
    handleSubmit() {
      const newUser = {
        name: this.name,
        email: this.email,
        phone: this.phone, 
      };
      this.$emit("addUser", newUser);
      this.name = "";
      this.email = "";
      this.phone = ""; 
    },
  },
};
</script>

<style scoped>
.form-container {
  max-width: 500px;
  margin: auto;
  background-color: #f8f9fa; /* Light background */
}

/* Custom input design */
.custom-input {
  border-radius: 10px;
  border: 1px solid #ced4da;
  padding: 10px;
  transition: border-color 0.3s, box-shadow 0.3s;
}

.custom-input:focus {
  border-color: #007bff;
  box-shadow: 0 0 5px rgba(0, 123, 255, 0.5);
}

/* Custom button design */
.custom-button {
  background-color: #007bff;
  border: none;
  border-radius: 10px;
  color: #fff;
  transition: background-color 0.3s, transform 0.3s;
}

.custom-button:hover {
  background-color: #0056b3;
  transform: translateY(-2px);
}

.custom-button:focus {
  box-shadow: 0 0 5px rgba(0, 123, 255, 0.5);
}
</style>
