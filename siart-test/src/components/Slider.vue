<script setup>

import { register } from 'swiper/element/bundle';
import { useSwiper } from 'swiper/vue';

import Card from '@/components/Card.vue'
import IconPrevious from '@/components/icons/IconPrevious.vue'
import IconNext from '@/components/icons/IconNext.vue'
import data from '@/data/data.json'

register();

defineProps({
  sliderTitle: {
    type: String,
    required: true
  },
})

const items = data.products;
const swiper = useSwiper();

</script>

<template>
  <section class="slider">
    <div class="slider__header">
      <h2 class="slider__title">{{ sliderTitle }}</h2>
      <div class="slider__buttons">
        <button class="slider__button slider__button_previous">
          <IconPrevious />
        </button>
        <button @click="swiper.slideNext()" class="slider__button slider__button_next">
          <IconNext />
        </button>
      </div>
    </div>
    <swiper-container slides-per-view="5" speed="500" loop="true" modules="[Pagination]" :pagination="true">
      <swiper-slide v-for="item in items" :key="item.id">
        <Card :key="item.id" :itemId="item.id" :itemTitle="item.title" :itemPrice="item.price"
          :itemOldPrice="item.oldPrice" :itemNumber="item.number" />
      </swiper-slide>
    </swiper-container>
  </section>
</template>

<style scoped>
.slider {
  padding: 4.2em 8.2em 2em 8.2em;
  background-color: var(--color-background-slider);
}

.slider__header {
  margin-bottom: 1.3em;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.slider__title {
  font-weight: 500;
  font-size: 1.75em;
  line-height: 1.3;
}

.slider__buttons {
  display: flex;
  border: 1px solid var(--color-light-grey);
  border-radius: 100px;
  padding: 0.25em;
}

.slider__button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background-color: transparent;
  width: 28px;
  height: 28px;
  border-radius: 50%;
  transition: .4s;
}

.slider__button:hover {
  background-color: var(--color-light-blue-hover);
}

.slider__button:focus-within {
  background-color: var(--color-light-blue-hover);
}

.slider__button:active {
  background-color: var(--color-light-blue);
}
</style>