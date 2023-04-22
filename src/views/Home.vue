<template>
  <div>
    <v-img
        lazy-src="../assets/banner.jpg"
        width="100%"
        height="450"
        src="../assets/banner.jpg"
    >
      <div class="fill-height bottom-gradient"></div>
    </v-img>
    <section style="padding-top: -8.5rem; margin-top: -8.5rem; position: relative; z-index: 2" class="white--text text-h4 font-weight-bold">
      <div class="container">
        <h1 style="line-height: 1.1">Gagafood - доставка от 15 минут!</h1>
      </div>
    </section>
    <section class="grey lighten-2 mt-0 pt-0 pb-2">
      <h2 class="mt-0 text-center" style="padding-top: 90px;">Закажите доставку прямо сейчас!</h2>
      <v-btn class="mb-8 mx-auto d-flex mt-5" style="width: 350px;" to="restaurants" large>Перейти к ресторанам <v-icon class="pl-2">mdi-store</v-icon></v-btn>
    </section>
    <section class="container">
      <h2 class="mb-6 mt-2 text-center d-none">Почему мы?</h2>
      <v-row
          class="mt-4"
          justify="center"
      >
        <v-col cols="12" sm="3">
          <p class="text-h3"><b>5000+</b></p>
          <span class="text-h5">заказов через наш сервис</span>
        </v-col>
        <v-col cols="12" sm="3">
          <p class="text-h3"><b>1500+</b></p>
          <span class="text-h5">положительных отзывов</span>
        </v-col>
        <v-col cols="12" sm="3">
          <p class="text-h3"><b>больше 10000</b></p>
          <span class="text-h5">людей доверяют нам уже в течение 5 лет работы на рынке</span>
        </v-col>
      </v-row>
    </section>
    <section class="container">
      <h2 class="mb-6 mt-2 text-center">Отзывы пользователей</h2>

      <v-row justify="center">
        <v-col cols="12" sm="4" v-for="comment in comments" :key="comment.id">
          <v-card
              class="mx-auto"
          >
            <v-card-text>
              <p class="text-h4 text--primary">
                {{ comment.name }}
              </p>
              <div class="text--primary">
                {{ comment.content }}
              </div>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
      <h3 class="text-center mt-4">Оставьте отзыв о нашей работе</h3>
      <v-form @submit.prevent="onSubmit">
        <v-container class="mx-auto" style="max-width: 400px;">
          <v-text-field
              label="Ваше имя"
              filled
              v-model="nameComment"
          ></v-text-field>
          <v-text-field
              label="Ваш email для обратной связи"
              type="email"
              filled
              v-model="emailComment"
          >
          </v-text-field>
          <v-textarea
              label="Ваше сообщение"
              filled
              v-model="textComment"
          ></v-textarea>
          <v-btn type="submit" width="100%">Отправить</v-btn>
        </v-container>
      </v-form>
    </section>
  </div>
</template>

<style>
.bottom-gradient {
  background-image: linear-gradient(to top, rgba(0, 0, 0, 0.6) 0%, transparent 150px);
}
</style>

<script>
import Data from "../assets/main.json"

export default {
  components: {
  },
  data() {
    return {
      comments: null,
      nameComment: null,
      textComment: null,
      emailComment: null
    }
  },
  methods: {
    onSubmit() {
      this.comments.push({
        name: this.nameComment,
        content: this.textComment
      })
      this.emailComment = null;
      this.nameComment = null;
      this.textComment = null;
    }
  },
  async mounted() {
    const data = Data;
    this.comments = data.comments
    console.log(data)
  }
}
</script>
