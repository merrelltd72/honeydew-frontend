<script>
import axios from "axios";
import HoneydewsIndex from "../HoneydewsIndex.vue";
import HoneydewNew from "../HoneydewNew.vue";
import HoneydewsShow from "./HoneydewsShow.vue";
import Modal from "./Modal.vue";

export default {
  components: {
    HoneydewsIndex,
    HoneydewNew,
    HoneydewsShow,
    Modal,
  },
  data: function () {
    return {
      honeydews: [],
      currentHoneydew: {},
      isHoneydewsShowVisible: false,
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
    handleShowHoneydew: function (honeydew) {
      console.log("handleShowHoneydew", honeydew);
      this.currentHoneydew = honeydew;
      this.isHoneydewsShowVisible = true;
    },
    handleClose: function () {
      this.isHoneydewsShowVisible = false;
    },
  },
};
</script>

<template>
  <main>
    <HoneydewNew v-on:createHoneydew="handleCreateHoneydew" />
    <HoneydewsIndex v-bind:honeydews="honeydews" v-on:showHoneydew="handleShowHoneydew" />
    <Modal v-bind:show="isHoneydewsShowVisible" v-on:close="handleClose">
      <HoneydewsShow v-bind:honeydew="currentHoneydew" />
    </Modal>
  </main>
</template>

<style></style>
