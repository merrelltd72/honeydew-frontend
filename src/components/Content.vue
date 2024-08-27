<script>
import axios from "axios";
import HoneydewsIndex from "../HoneydewsIndex.vue";

export default {
  components: {
    HoneydewsIndex,
  },
  data: function () {
    return {
      honeydews: [],
    };
  },
  created: function () {
    this.handleIndexHoneydews();
  },
  methods: {
    handleIndexHoneydews: function () {
      axios.get("http://localhost:5000/honeydews.json").then((response) => {
        console.log("honeydews index", response);
        this.honeydews = response.data;
      });
    },
  },
};
</script>

<template>
  <main>
    <HoneydewsIndex v-bind:honeydews="honeydews" />
  </main>
</template>

<style></style>
