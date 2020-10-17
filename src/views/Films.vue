<template>
  <div class="films">
    <div v-if="start" class="start">
      Угадай фильм по фото
      <button @click="start = false" class="button">
        Начать Игру
      </button>
    </div>
    <div v-else-if="!start && (lifes + 1)" class="game">
      <div class="progress">Счет: {{ level }}</div>
       <div class="lifes">
        <span :class="{ truble: lifes < 3 }">&#10084;</span>
        <span :class="{ truble: lifes < 2 }">&#10084;</span>
        <span :class="{ truble: lifes < 1 }">&#10084;</span>
      </div>
      <div class="level" v-if="levels[level]">
        <div class="img-container">
          <img :src="levels[level].img" alt="img" />
        </div>
        <div class="questions">
          <button 
            v-for="ques in levels[level].questions" 
            :key="ques.title" 
            class="question"
            @click="answer(ques.answer)"
          >
            {{ ques.title }}
          </button>
        </div>
      </div>
      <div class="win" v-else>
        <div>Поздравляем Вы прошли игру!!!</div>
        <button @click="restart()" class="button">На главную</button>
      </div>
    </div>
    <div v-else class="lose">
      <div>Вы проиграли</div>
      <div>Счет {{level}}</div>
      <button @click="restart()" class="button">На главную</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Films",
  data() {
    return {
      start: true,
      levels: [
        {
          img: "/img/lev1.jpg",
          questions: [
            { title: "Командо", answer: false },
            { title: "Спасти рядового Райана", answer: false },
            { title: "Форест Гамп", answer: true },
            { title: "Рэмбо", answer: false }
          ]
        },
        {
          img: "/img/lev2.jpg",
          questions: [
            { title: "Титаник", answer: false },
            { title: "Пираты Карибского моря", answer: false },
            { title: "Остров Сокровищ", answer: false },
            { title: "Жизнь Пи", answer: true }
          ]
        },
        {
          img: "/img/lev3.jpg",
          questions: [
            { title: "Аватар", answer: true },
            { title: "Вертикальный взлет", answer: false },
            { title: "Авиатор", answer: false },
            { title: "Экипаж", answer: false }
          ]
        },
        {
          img: "/img/lev4.jpg",
          questions: [
            { title: "Разрушение", answer: false },
            { title: "Планета Обезьян", answer: false },
            { title: "Исходный код", answer: true },
            { title: "Дежа вю", answer: false }
          ]
        }
      ],
      level: 0,
      lifes: 3
    };
  },
  methods: {
    answer(a) {
      if (a) {
        this.level += 1;
      }
      else {
        this.lifes -= 1;
      }
    },
    restart() {
      window.location.reload()
    }
  }
};
</script>

<style lang="scss" scoped>
@mixin menu($color) {
  color: #fff;
  font-size: 50px;
  text-shadow: 2px 2px 4px $color;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 13%;
}
.films {
  background-image: url("../assets/film1.jpg");
  height: 100vh;
  padding: 20px;
  box-sizing: border-box;
}
.start {
  @include menu(blue);
}
.lose {
  @include menu(red);
}
.win {
  @include menu(green);
}
.button {
  background: blue;
  color: white;
  padding: 10px 15px;
  font-size: 20px;
  border-radius: 4px;
  border: 2px solid #fff;
  cursor: pointer;
  margin-top: 25px;
  &:hover {
    transition: 0.3s;
    opacity: 0.8;
  }
}

.questions {
  margin-top: 40px;
  display: flex;
  width: 100%;
  justify-content: space-evenly;
}
.question {
  background-color: #FFF;
  border: none;
  padding: 5px 10px;
  font-size: 20px;
  border-radius: 4px;
  cursor: pointer;
  outline: none;
  transition: 0.3s;
  &:hover {
    background-color: #C1C1C1;
    transform: scale(1.1)
  }
}
.img-container {
  height: 415px;
}
img {
  max-width: 570px;
  border: 3px solid #FFF;
}
.progress {
  position: absolute;
  color: #FFF;
  font-size: 25px;
  font-weight: 600;
  background: #000;
  padding: 5px 10px;
  border-radius: 4px;
}
.lifes {
  position: absolute;
  right: 20px;
  color: red;
  font-size: 50px;
  width: 180px;
  background: rgba(255, 255, 255, .6);
  border-radius: 4px;
  display: flex;
  justify-content: space-around;
  & span {
    cursor: default;
  }
  & .truble {
    color: gray;
  }
}
</style>