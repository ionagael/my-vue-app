<template>
  <div class="stack-small">
    <div class="custom-checkbox">
      <input
        type="checkbox"
        :id="id"
        :checked="completed"
        @change="$emit('course-completed')"
        class="checkbox"
      />
      <label :for="id" class="checkbox-label">{{ title }}</label>
    </div>
    <button type="button" class="btn btn__danger" @click="$emit('course-deleted')">
      Delete <span class="visually-hidden">{{ title }}</span>
    </button>
  </div>
</template>

<script>
export default {
  props: {
    id: { required: true, type: String },
    title: { required: true, type: String },
    completed: { default: false, type: Boolean },
  },
};
</script>

<style scoped>
.stack-small {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #ddd;
}
.custom-checkbox {
  display: flex;
  align-items: center;
}
.checkbox {
  margin-right: 10px;
}
.checkbox-label {
  font-weight: 500;
    color: black;
}
.btn__danger {
  background-color: #e63946;
  color: #black;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}
</style>
