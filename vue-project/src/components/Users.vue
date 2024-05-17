<template>
  <div>
    <h3>{{ user.name }}</h3>
    <p>
      {{ user.email }} - <b>{{ user.password }}</b>
    </p>
    <button @click="deleteUser(index)">Delete</button>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    },
    deleteUser: {
      type: Function,
      required: true,
    },
  },
};
</script>

<style scoped></style>
