<template>
  <v-app>
    <header>
    <v-app-bar
        class="d-print-none"
        app
        color="pink darken-1"
        dark
    >
      <div class="d-flex align-center">
        <v-img
            alt="Vuetify Name"
            class="shrink mt-1 hidden-sm-and-down"
            contain
            min-width="100"
            src="/img/logo.png"
            width="160"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
          class="mx-2"
          to="/"
          text
      >
        <span>Главная</span>
      </v-btn>
      <v-btn
          class="mx-2"
          to="/restaurants"
          text
      >
        <span>Все рестораны</span>
      </v-btn>
      <v-btn
          class="mx-2"
          to="/about"
          text
      >
        <span>Привет, Алексей</span>
      </v-btn>
      <v-btn
          class="mx-2"
          href="https://github.com/kingdomstay/exam-gagafood"
          text
      >
        <span>Github</span>
      </v-btn>
      <v-btn
          class="mx-2"
          href="/main.json"
          text
      >
        <span>JSON</span>
      </v-btn>
    </v-app-bar>
    </header>

    <main>
    <v-main>
      <router-view></router-view>
    </v-main>
    </main>

    <footer>
      <v-footer padless>
        <v-col
            class="text-center"
            cols="12"
        >
          {{ new Date().getFullYear() }} — <strong>ИП Леди Гага</strong>.
        </v-col>
      </v-footer>
    </footer>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  components: {
  },

  data: () => ({
    //
  }),
};
</script>
