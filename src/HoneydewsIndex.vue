<script>
export default {
  props: {
    honeydews: Array,
  },
};
</script>

<template>
  <div>
    <h1>All Honeydews</h1>
    <div v-for="honeydew in honeydews" v-bind:key="honeydew.id">
      <h2>{{ honeydew.name }}</h2>
      <p>{{ honeydew.description }}</p>
      <button v-on:click="$emit('showHoneydew', honeydew)">More info</button>
    </div>
  </div>
</template>

<style></style>
