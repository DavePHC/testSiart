<script setup>

import {ref} from 'vue';
import { register } from 'swiper/element/bundle';

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

const breakpoints = ref({
  320: {
    slidesPerView: 2,
    spaceBetween: 10,
  },
  640: {
    slidesPerView: 3,
    spaceBetween: 10,
  },
  768: {
    slidesPerView: 4,
    spaceBetween: 15,
  },
  1024: {
    slidesPerView: 5,
    spaceBetween: 10,
    pagination: false
  },
  1400: {
    slidesPerView: 5,
    spaceBetween: 15,
    pagination: false
  },
});

</script>

<template>
  <section class="slider">
    <div class="slider__header">
      <h2 class="slider__title">{{ sliderTitle }}</h2>
      <div class="slider__buttons">
        <button class="slider__button slider__button_previous">
          <IconPrevious />
        </button>
        <button id="sliderB" class="slider__button slider__button_next">
          <IconNext />
        </button>
      </div>
    </div>
    <div class="slider__body">
      <swiper-container
        spaceBetween="5"
        speed="400"
        :pagination="true"
        :breakpoints="breakpoints"
        :navigation="{ nextEl: '.slider__button_next', prevEl: '.slider__button_previous' }">
        <swiper-slide v-for="item in items" key="key">
          <Card :key="item.id" :itemId="item.id" :itemTitle="item.title" :itemPrice="item.price"
            :itemOldPrice="item.oldPrice" :itemNumber="item.number" />
        </swiper-slide>
      </swiper-container>
    </div>
  </section>
</template>

<style>

  .swiper {
    overflow: visible;
  }

  .swiper-pagination {
    background-color: red !important;
  }

  .slider {
    padding: 24px 20px;
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
    display: none;
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

  .slider__body {
    padding-bottom: 18px;
    overflow: hidden;
  }

  @media (min-width: 768px) {

    .slider__buttons {
      display: flex;
    }

  }

</style>
