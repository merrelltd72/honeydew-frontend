<script>
export default {
  props: {
    photo: Object,
  },
};
</script>

<template>
  <div>
    <h1>Your Honeydew:</h1>
    <p>{{ honeydew.name }}</p>
    <p>{{ honeydew.completed }}</p>
    <p>{{ honeydew.deadline }}</p>
    <p>{{ honeydew.description }}</p>
    <p>{{ honeydew.priority }}</p>
  </div>
</template>

<style></style>