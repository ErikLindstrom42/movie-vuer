<template>
  <div>
    <div v-if="reviews && reviews.length > 0">
      <h3 class="red--text">User Reviews</h3>
      <v-list three-line>
        <v-list-item v-for="review in reviews" :key="review.id">
          <v-list-item-avatar>
            <v-img
              :src="`https://image.tmdb.org/t/p/w200${review.author_details.avatar_path}`"
            ></v-img>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title>{{ review.author }}</v-list-item-title>
            <v-list-item-subtitle>
              {{ formatDate(review.created_at) }}
            </v-list-item-subtitle>
            <div class="mt-2">{{ review.content }}</div>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </div>
    <div v-if="reviews && reviews.length === 0 && movieDetails">
      <h3>No reviews available</h3>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import { dateMixin } from "../mixins/movieMixins";
export default {
  mixins: [dateMixin],
  computed: {
    ...mapState(["reviews", "movieDetails"]),
  },
};
</script>