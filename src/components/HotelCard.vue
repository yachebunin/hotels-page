<template>
  <div class="card">
    <div class="card-header">
      <div class="card-header__info">
        <h3 class="card-header__title">{{ hotel.name }}</h3>
        <div>
          <span
              v-for="star in 5"
              :key="'star-' + star"
              class="card-header__star"
          >
            <img :src="star <= hotel.stars ? require('@/assets/coloredStar.svg') : require('@/assets/unColoredStar.svg')"/>
          </span>
        </div>
        <p class="card-header__type">{{ hotel.type }}</p>
        <p class="card-header__reviews">{{ hotel.reviews_amount }}</p>
        <p class="card-header__country"><img :src="require('@/assets/point.svg')" /> <span>{{ hotel.country }}</span></p>
      </div>
      <div class="card-header__price">
        <h3 class="card-header__price-value">{{ hotel.min_price }} ₽</h3>
        <p class="card-header__price-text">Цена за 1 ночь</p>
      </div>
    </div>
    <div class="card-body">
      <p class="card-body__desc">{{ hotel.description }}</p>
      <button class="card-body__btn"><img :src="require('@/assets/done.svg')" /> <span>Забронировано</span></button>
    </div>
  </div>

<!--  TODO доделать разный тип кнопок-->
</template>

<script>
  export default {
    name: 'HotelCard',

    data: () => ({
    }),

    props: {
      hotel: {
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
      }
    }
  }
</script>

<style lang="scss">
@import "@/styles/_variables.scss";

.card {
  display: flex;
  flex-direction: column;
  border: 1px solid #EAEAEA;
  border-radius: 15px;
  padding: 25px;

  &-header, &-body {
    display: flex;
    justify-content: space-between;
  }

  &-header {
    align-items: center;
    margin-bottom: 16px;
    &__info {
      display: grid;
      grid-template-rows: repeat(2, auto);
      grid-template-columns: repeat(4, auto);
      grid-column-gap: 15px;
      grid-row-gap: 8px;
      align-items: center;
    }
    &__title {
      grid-column-start: 1;
      grid-column-end: 5;
      font-weight: 700;
      font-size: 20px;
      line-height: 26px;
      color: $text-main;
    }
    &__star:not(:last-child) {
      margin-right: 6px;
    }
    &__type, &__reviews {
      font-weight: 400;
      font-size: 14px;
      line-height: 18px;
      color: $text-secondary; // TODO добавить шрифты
    }
    &__reviews {
      position: relative;
      padding-left: 2px;
    }
    &__reviews:before {
      content: '';
      position: absolute;
      left: -8px;
      top: 50%;
      transform: translateY(-50%);
      width: 4px;
      height: 4px;
      background: #949494;
      border-radius: 100%;
    }
    &__country {
      display: flex;
      align-items: center;
      font-weight: 400;
      font-size: 14px;
      line-height: 21px;
      color: $text-main;
      img {
        margin-right: 8px;
      }
    }
    &__price {
      display: flex;
      flex-direction: column;
      align-items: end;
    }
    &__price-value {
      font-weight: 700;
      font-size: 25px;
      line-height: 32px;
      text-align: right;
      color: $text-main;
    }
    &__price-text {
      font-weight: 400;
      font-size: 12px;
      line-height: 16px;
      color: $text-secondary;
    }
  }

  &-body {
    &__desc {
      max-width: 69%;
      font-weight: 400;
      font-size: 16px;
      line-height: 24px;
      color: $text-main;
    }
    &__btn {
      display: flex;
      align-items: center;
      max-height: 40px;
      padding: 10px 30px 12px;
      color: #00BB6D;
      background: rgba(#00BB6D, 0.1);
      font-weight: 400;
      font-size: 14px;
      line-height: 18px;
      border-radius: 12px;
      img {
        margin-right: 10px;
      }
    }
  }
}
</style>