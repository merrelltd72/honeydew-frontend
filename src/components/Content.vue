<script>
  import HoneydewsIndex from '../HoneydewsIndex.vue';

  export default {
    components: {
      HoneydewsIndex,
    },
    data: function () {
      return {
        honeydews: [
          { id: 1, name: "test1"},
          { id: 2, name: "test2"},
        ],
      };
    },
  };
</script>

<template>
  <main>
    <HoneydewsIndex v-bind:honeydews="honeydews" />
  </main>
</template>

<style></style>
