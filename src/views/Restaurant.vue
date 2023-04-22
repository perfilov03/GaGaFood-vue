<template>
  <div class="container">
    <v-row>
      <v-col cols="12" sm="4">
        <v-sheet
            elevation="8"
            rounded
            class="rounded-xl pa-6 d-flex flex-column"
        >
          <v-img
              max-height="45vh"
              class="my-4"
              :src="require(`../assets/${restaurant.banner}`)"
          ></v-img>
          <h1 class="text-center">{{restaurant.name}}</h1>
          <v-chip-group
              active-class="deep-purple accent-4 white--text"
              column
          >
            <v-chip v-if="restaurant.free_delivery">Бесплатная доставка</v-chip>
          </v-chip-group>
          <div class="my-1 text-subtitle-1">
            <span v-if="restaurant.cost === 1">$</span><span v-else-if="restaurant.cost === 2">$$</span><span v-else-if="restaurant.cost === 3">$$$</span> • {{restaurant.name_kitchen}}
          </div>

          <div>{{restaurant.description}}</div>

          <h2 class="text-center">Меню</h2>

          <v-card>
            <v-list-item three-line v-for="menu in restaurant.menu" :key="menu.id">
              <v-list-item-content>
                <v-list-item-title>{{menu.name}}</v-list-item-title>
                <v-list-item-subtitle><v-btn @click="editProduct(id)">Редактировать</v-btn><v-btn @click="$delete()">Удалить</v-btn></v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-card>
        </v-sheet>
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
      restaurant: null,
    }
  },
  methods: {
    removeElement: function (index) {
      this.items.splice(index, 1);
    },
    editProduct(id) {
      console.log(id)
    }
  },
  created() {
    const data = Data.restaurants;
    this.restaurant = data[this.$route.params.id];
  }
}
</script>
