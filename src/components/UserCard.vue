<template>
  <div class="card user-card shadow-sm">
    <div class="card-body">
      <template v-if="isEditing">
        <h5 class="card-title">Edit User</h5>
        <form @submit.prevent="submitEdit" class="edit-form">
          <div class="mb-3">
            <label for="editName" class="form-label">Name</label>
            <input
              v-model="editableUser.name"
              id="editName"
              type="text"
              class="form-control"
              required
            />
          </div>
          <div class="mb-3">
            <label for="editEmail" class="form-label">Email</label>
            <input
              v-model="editableUser.email"
              id="editEmail"
              type="email"
              class="form-control"
              required
            />
          </div>
          <div class="mb-3">
            <label for="editPhone" class="form-label">Phone Number</label>
            <input
              v-model="editableUser.phone"
              id="editPhone"
              type="tel"
              class="form-control"
              required
            />
          </div>
          <div class="d-flex justify-content-end">
            <button type="submit" class="btn btn-success btn-sm me-2">
              Save
            </button>
            <button
              @click="cancelEdit"
              type="button"
              class="btn btn-secondary btn-sm"
            >
              Cancel
            </button>
          </div>
        </form>
      </template>
    <template v-else>
  <h5 class="card-title d-flex justify-content-between align-items-center">
    {{ user.name }}
    
  </h5>
  <p class="card-text">
    <i class="bi bi-envelope me-2"></i>{{ user.email }}
  </p>
  <p class="card-text">
    <i class="bi bi-telephone me-2"></i>{{ user.phone }}
  </p>
 <div class="d-flex justify-content-end">
  <button @click="startEdit" class="btn btn-outline-primary btn-sm me-2">
    <i class="bi bi-pencil-square me-1"></i>Update
  </button>
  <button @click="$emit('deleteUser')" class="btn btn-outline-danger btn-sm">
    <i class="bi bi-trash me-1"></i>Delete
  </button>
</div>


</template>

    </div>
  </div>
</template>

<script>
export default {
  props: {
    user: Object,
  },
  data() {
    return {
      isEditing: false,
      editableUser: { ...this.user }, 
    };
  },
  methods: {
    startEdit() {
      this.isEditing = true;
      this.editableUser = { ...this.user }; 
    },
    cancelEdit() {
      this.isEditing = false;
      this.editableUser = { ...this.user };
    },
    submitEdit() {
      this.$emit("updateUser", this.editableUser);
      this.isEditing = false; 
    },
  },
};
</script>
