<template>
  <div class="films">
    <button v-if="start" @click="start = !start" class="button_start">
			Начать Игру
		</button>
    <div v-if="!start" class="game">
			<img src="../assets/lev1.jpg" alt="img">
		</div>
  </div>
</template>

<script>
export default {
  name: "Films",
  data() {
    return {
      start: true
    };
  }
};
</script>

<style lang="scss" scoped>
.films {
  background-image: url("../assets/film1.jpg");
  height: 100vh;
}
.button_start {
  background: blue;
  color: white;
  padding: 10px 15px;
  font-size: 20px;
  border-radius: 4px;
  border: 2px solid #fff;
  cursor: pointer;
  margin-top: 20%;
  &:hover {
    transition: 0.3s;
    opacity: 0.8;
  }
}
</style>