<template>
  <div>
    <v-card class="flex-grow-1 flex-shrink-1 ma-4" elevation="12">
      <v-carousel height="250px" hide-delimiter-background show-arrows-on-hover>
        <v-carousel-item
          v-for="(image, i) in images"
          :key="i"
          :src="image.src"
          class="relative"
        >
          <v-tooltip v-model="show" bottom>
            <template v-slot:activator="{ on, attrs }">
              <v-chip
                v-bind="attrs"
                v-on="on"
                v-if="certified == 1"
                class="ma-2 absolute"
                color="green"
                text-color="white"
              >
                <v-avatar left>
                  <v-icon>mdi-check-circle</v-icon>
                </v-avatar>
                Certified
              </v-chip>
            </template>
            <span>This wing has been controlled by a professional.</span>
          </v-tooltip>
        </v-carousel-item>
      </v-carousel>
      <v-card-title class="py-3"
        >{{ brand }}, {{ model }} <v-spacer></v-spacer
        ><v-btn icon class="d-flex" @click="isFavorite = !isFavorite">
          <v-icon class="font-weight-bold red--text">{{
            this.isFavorite ? "mdi-heart" : "mdi-heart-outline"
          }}</v-icon>
        </v-btn></v-card-title
      >
      <v-card-text class="text--primary relative">
        <div class="pb-1">
          <v-icon class="mr-2">mdi-scale</v-icon>{{ weigthRangeMin }} -
          {{ weigthRangeMax }} kg
        </div>
        <div class="pb-1">
          <v-icon class="mr-2">mdi-calendar</v-icon>{{ year }}
        </div>
        <div class="pb-1">
          <v-icon class="mr-2">mdi-clock-outline</v-icon>{{ hours }} hours
        </div>
        <div class="pb-1">
          <v-icon class="mr-2">mdi-currency-usd</v-icon>{{ price }} euros
        </div>
        <div class="pb-1">
          <v-icon class="mr-2">mdi-shape</v-icon>{{ category }}
        </div>
        <div class="pb-1">
          <v-icon class="mr-2">mdi-map-marker</v-icon>{{ country }}, {{ town }}
        </div>
        <!--         <div class='ml-2 pb-2'>Condition:</div>
        <div class="d-flex justify-space-around">
          <v-icon :style = "[ (condition == 1)?{border: '3px solid forestgreen', color: 'forestgreen', borderRadius: '50%', padding: '2px'}:{} ]">mdi-emoticon-cool-outline</v-icon
          ><v-icon :style = "[ (condition == 2)?{border: '3px solid green', color: 'green', borderRadius: '50%', padding: '2px'}:{} ]">mdi-emoticon-excited-outline</v-icon
          ><v-icon :style = "[ (condition == 3)?{border: '3px solid gold', color: 'gold', borderRadius: '50%', padding: '2px'}:{} ]">mdi-emoticon-happy-outline</v-icon
          ><v-icon :style = "[ (condition == 4)?{border: '3px solid orange', color: 'orange', borderRadius: '50%', padding: '2px'}:{} ]">mdi-emoticon-neutral-outline</v-icon
          ><v-icon :style = "[ (condition == 5)?{border: '3px solid red', color: 'red', borderRadius: '50%', padding: '2px'}:{} ]">mdi-emoticon-dead-outline</v-icon>
        </div> -->
      </v-card-text>
      <v-card-actions class="pa-5 pt-0 d-flex justify-center">
        <v-btn color="primary">
          <v-icon class="mr-2">mdi-book-search-outline</v-icon> More information
        </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
export default {
  props: [
    "brand",
    "model",
    "weigthRangeMin",
    "weigthRangeMax",
    "year",
    "hours",
    "price",
    "category",
    "country",
    "town",
    "condition",
    "certified"
  ],
  data() {
    return {
      isFavorite: false,
      images: [
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg"
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/sky.jpg"
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/bird.jpg"
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/planet.jpg"
        }
      ]
    };
  },
  method: {}
};
</script>

<style scoped lang="scss">
.relative {
  position: relative;
}
.absolute {
  position: absolute;
  top: 0;
  right: 0;
}
</style>
