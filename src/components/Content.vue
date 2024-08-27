<script>
import axios from "axios";
import HoneydewsIndex from "../HoneydewsIndex.vue";
import HoneydewNew from "../HoneydewNew.vue";

export default {
  components: {
    HoneydewsIndex,
    HoneydewNew,
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
    handleCreateHoneydew: function (params) {
      axios
        .post("http://localhost:5000/honeydews.json", params)
        .then((response) => {
          console.log("Honeydews create", response);
          this.honeydews.push(response.data);
        })
        .catch((error) => {
          console.log("photos create error", error.response);
        });
    },
  },
};
</script>

<template>
  <main>
    <HoneydewNew v-on:createHoneydew="handleCreateHoneydew" />
    <HoneydewsIndex v-bind:honeydews="honeydews" />
  </main>
</template>

<style></style>
