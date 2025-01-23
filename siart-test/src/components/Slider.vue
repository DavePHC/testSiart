<script setup>
import Card from '@/components/Card.vue'
import IconPrevious from '@/components/icons/IconPrevious.vue'
import IconNext from '@/components/icons/IconNext.vue'

defineProps({
  sliderTitle: {
    type: String,
    required: true
  },
})
</script>

<template>
  <section class="slider">
    <div class="slider__header">
      <h2 class="slider__title">{{ sliderTitle }}</h2>
      <div class="slider__buttons">
        <button class="slider__button">
          <IconPrevious/>
        </button>
        <button class="slider__button">
          <IconNext/>
        </button>
      </div>
    </div>
    <div class="slider__track">
        <Card
          cardTitle="Тонометр механический CS Medica CS-106 с фонедоскопом dfdf dfdf dfd"
          cardPrice=234
        />
    </div>
  </section>
</template>

<style scoped>

.slider {
  padding: 4.2em 8.2em 2em 8.2em;
  background-color: var(--color-background-slider);
}

.slider__header {
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
  border: 1px solid var(--color-border-light-grey);
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
  background-color: var(--color-button-slider-hover);
}

.slider__button:focus-within {
  background-color: var(--color-button-slider-hover);
}

.slider__button:active {
  background-color: var(--color-button-slider-active);
}

.slider__track {
  padding: 1.3em 0;
}

</style>