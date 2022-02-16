<template>
  <div class="input-group cs-select mt-2">
    <label class="input-group-text" for="inputGroupSelect01">Generi</label>
    <select
      v-model="value"
      @change="getOptions"
      class="form-select"
      id="inputGroupSelect03"
      :selected="selected"
    >
      <option value="">{{ placeholder }}</option>
      <option v-for="(genre, index) in genres" :key="index" :value="genre">
        {{ genre }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "Filter",
  props: ["placeholder", "genres"],
  data() {
    return {
      value: "",
    };
  },

  methods: {
    getOptions() {
      this.$emit("getOption", this.value);
    },
  },
};
</script>

<style>
</style>