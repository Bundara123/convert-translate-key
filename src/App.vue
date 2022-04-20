<template>
  <div id="app">
    <textarea v-model="text" />
    <div @click="selectAndCopy" ref="ele">
      {{ display }}
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      text: "",
    };
  },
  computed: {
    display() {
      return this.text
        .toLowerCase()
        .replace(/[^a-zA-Z0-9 ]/g, "")
        .replaceAll(" ", "_");
    },
  },
  components: {},
  methods: {
    selectAndCopy($event) {
      window.getSelection().selectAllChildren(this.$refs.ele);
      document.execCommand("copy");
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
