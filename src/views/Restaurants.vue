<template>
  <div class="container">
    <h1>Рестораны</h1>
      <v-form class="pa-6">
        <v-row>
          <v-col
              cols="12"
              sm="3"
          >
            <v-text-field
                filled
                v-model="searchRestaurant"
                label="Поиск по названию"
            ></v-text-field>
          </v-col>
          <v-col
              cols="12"
              sm="3"
          >
            <v-select
                :items="sortItems"
                filled
                label="Сортировать по"
            ></v-select>
          </v-col>
          <v-col
              cols="12"
              sm="2"
          >
            <v-checkbox
                v-model="free_delivery"
                label="Бесплатная доставка"
                hide-details="auto"
            ></v-checkbox>
          </v-col>
        </v-row>
      </v-form>

      <v-row v-if="!searchRestaurant">
        <v-col cols="12" sm="3" v-for="restaurant in restaurants" :key="restaurant.id">
          <v-card
              class="my-3"
          >
            <template slot="progress">
              <v-progress-linear
                  color="deep-purple"
                  height="10"
                  indeterminate
              ></v-progress-linear>
            </template>

            <v-img
                height="250"
                :src="require(`../assets/${restaurant.banner}`)"
            ></v-img>

            <v-card-title>{{restaurant.name}}</v-card-title>

            <v-card-text>

              <div class="my-1 text-subtitle-1">
                <span v-if="restaurant.cost === 1">$</span><span v-else-if="restaurant.cost === 2">$$</span><span v-else-if="restaurant.cost === 3">$$$</span> • {{restaurant.name_kitchen}}
              </div>

              <div>{{restaurant.description}}</div>
            </v-card-text>

            <v-divider class="mx-4"></v-divider>

            <v-card-title>Особенности</v-card-title>

            <v-card-text>
              <v-chip-group
                  active-class="deep-purple accent-4 white--text"
                  column
              >
                <v-chip v-if="restaurant.free_delivery">Бесплатная доставка</v-chip>
              </v-chip-group>
            </v-card-text>

            <v-card-actions>
              <v-btn
                  color="pink lighten-2"
                  text
                  :to="'restaurants/' + restaurant.id"
              >
                Перейти в меню
                <v-icon class="pl-2">mdi-coffee</v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    <v-row v-if="searchRestaurant">
      <v-col cols="12" sm="3" v-for="restaurant in filterSearch" :key="restaurant.id">
        <v-card
            class="my-3"
        >
          <template slot="progress">
            <v-progress-linear
                color="deep-purple"
                height="10"
                indeterminate
            ></v-progress-linear>
          </template>

          <v-img
              height="250"
              :src="require(`../assets/${restaurant.banner}`)"
          ></v-img>

          <v-card-title>{{restaurant.name}}</v-card-title>

          <v-card-text>

            <div class="my-1 text-subtitle-1">
              <span v-if="restaurant.cost === 1">$</span><span v-else-if="restaurant.cost === 2">$$</span><span v-else-if="restaurant.cost === 3">$$$</span> • {{restaurant.name_kitchen}}
            </div>

            <div>{{restaurant.description}}</div>
          </v-card-text>

          <v-divider class="mx-4"></v-divider>

          <v-card-title>Особенности</v-card-title>

          <v-card-text>
            <v-chip-group
                active-class="deep-purple accent-4 white--text"
                column
            >
              <v-chip v-if="restaurant.free_delivery">Бесплатная доставка</v-chip>
            </v-chip-group>
          </v-card-text>

          <v-card-actions>
            <v-btn
                color="pink lighten-2"
                text
                :to="'restaurants/' + restaurant.id"
            >
              Перейти в меню
              <v-icon class="pl-2">mdi-coffee</v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import Data from "../assets/main.json"

export default {
  components: {
  },
  data() {
    return {
      sortItems: ['По возрастанию', 'По убыванию'],
      restaurants: null,
      searchRestaurant: null,
      free_delivery: false
    }
  },
  methods: {
  },
  computed: {
    filterSearch() {
      return this.restaurants.filter(restaurant => {
        return !this.searchRestaurant ||
            restaurant.name.toLowerCase().indexOf(this.searchRestaurant.toLowerCase()) > -1
      })
    },
    /*sortedArray: function() {
      function compare(a, b) {
        if (a.name < b.name)
          return -1;
        if (a.name > b.name)
          return 1;
        return 0;
      }
      // eslint-disable-next-line vue/no-side-effects-in-computed-properties
      return this.restaurants.sort(compare);
    }*/
  },
  async mounted() {
    const data = Data;
    this.restaurants = data.restaurants;
  }
}
</script>
