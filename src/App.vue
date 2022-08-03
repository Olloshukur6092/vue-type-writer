<template>
  <TheHome v-if="home" :startGame="startGame" />
  <TheTypeWriterForm v-if="writer" :getHome="getHome" />
</template>

<script>

import TheTypeWriterForm from "@/components/TheTypeWriterForm";
import TheHome from "@/components/containers/TheHome";

export default {
  name: "App",
  components: {
    TheHome,
    TheTypeWriterForm,
  },
  data() {
    return {
      home: true,
      writer: false
    }
  },
  methods: {
    startGame() {
      this.writer = !this.writer
      this.home = !this.home
    },
    getHome() {
      this.home = !this.home
      this.writer = !this.writer
    }
  },
};
</script>

<style>
</style>
