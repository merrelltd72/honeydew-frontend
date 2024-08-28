<script>
export default {
  data: function () {
    return {
      newHoneydewParams: {},
    };
  },
  methods: {
    handleSubmit: function () {
      this.$emit("createHoneydew", this.newHoneydewParams);
      this.newHoneydewParams = {};
    },
  },
};
</script>

<template>
  <div>
    <h1>New Honeydew</h1>
    <form v-on:submit.prevent="handleSubmit">
      <fieldset>
        <legend>Enter your new Honeydew:</legend>
        <div>
          Name:
          <input name="name" type="text" v-model="newHoneydewParams.name" />
        </div>
        <div>
          Description:
          <input
            name="description"
            type="text"
            v-model="newHoneydewParams.description"
          />
        </div>
        <div>
          Priority:
          <input
            name="priority"
            type="text"
            v-model="newHoneydewParams.priority"
          />
        </div>
        <button type="submit">Create Honeydew!</button>
      </fieldset>
    </form>
  </div>
</template>

<style></style>
