<template>
  <div class="bg-blue d-flex justify-content-between">
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/Logo_of_RAI_%282016%29.svg/768px-Logo_of_RAI_%282016%29.svg.png"
      class="img-fluid ms-3"
      alt="whatsapp"
    />
    <Filtered
      placeholder="Scegli un genere"
      :genres="genres"
      @getOption="getOption"
    />
  </div>
</template>

<script>
import Filtered from "./Filter.vue";
export default {
  name: "Header",
  props: ["genres"],
  components: {
    Filtered,
  },
  data() {
    return {};
  },
  methods: {
    getOption(value) {
      this.$emit("getOption", value);
    },
  },
};
</script>

<style  lang='scss'>
.bg-blue {
  background-color: #00009a;
}
img {
  width: 50px;
}

.cs-select {
  flex-basis: 200px;
  height: 25px;
  margin-right: 100px;
}
</style>