<template>
  <div class="home">
    <button @click="startGame" class="btn btn-outline-light">Start Game!</button>
    <button @click="close" class="btn btn-outline-light ms-2">Close Page!</button>
  </div>
</template>

<script>
export default {
  name: "TheHome",
  props: {
    startGame: {type: Function}
  },
  methods: {
    close() {
      window.close()
    }
  }
}
</script>

<style scoped>
.home {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background: rgba(0, 0, 0);
}
.home .btn {
  width: 250px;
  height: 70px;
  font-size: 30px;
}


</style>