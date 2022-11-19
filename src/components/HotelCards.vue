<template>
  <div class="cards">
    <HotelCard
        v-for="(hotel, index) in hotels"
        :key="'hotel-' + index"
        :hotel="hotel"
    />
  </div>
</template>

<script>
import HotelCard from "@/components/HotelCard";

export default {
  name: 'HotelCards',

  data: () => ({
  }),

  props: {
    hotels: [{
      name: String,
      country: String,
      address: String,
      stars: Number,
      type: String,
      description: String,
      services: [String],
      min_price: Number,
      currency: String,
      rating: Number,
      reviews_amount: Number,
      last_review: String
    }]
  },

  components: {
    HotelCard
  }
}
</script>

<style lang="scss">
.cards {
  display: flex;
  flex-direction: column;

  .card:not(:last-child) {
    margin-bottom: 15px;
  }
}
</style>