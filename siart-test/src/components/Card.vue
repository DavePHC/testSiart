<script setup>
  import IconQuickView from '@/components/icons/IconQuickView.vue'

  defineProps({
    cardTitle: {
      type: String,
      required: true
    },
    cardPrice: {
      type: String,
      required: true
    }
  })


</script>

<template>
  <article class="card">
    <div class="card__head">
      <button class="card__quick-view">
        <IconQuickView/>
        <span>Быстрый просмотр</span>
      </button>
      <img class="card__image" src="../assets/images/1.png" :alt="cardTitle">
    </div>
    <div class="card__body">
      <h3 class="card__title" :title="`${ cardTitle }`">{{ cardTitle }}</h3>
      <div class="stickers">
        <span>В наличии</span>
        <span>Хит</span>
        <span>Новинка</span>
        <span>Акция</span>
      </div>
      <span>{{ cardPrice }} ₽ шт</span>
    </div>
  </article>
</template>

<style scoped lang="scss">

.card {
  padding: 0.5em 0.75em;
  width: 100%;
  max-width: 316px;
  background-color: var(--color-white);
  border-radius: 1em;
  box-shadow: 0 0 10 0 rgba(28, 45, 64, .05);
}

.card__head {
  position: relative;
}

.card__image {
  max-width: 100%;
  height: auto;
}

.card__head:hover .card__quick-view {
  opacity: 1;
  visibility: visible;
  user-select: unset;
}

.card__quick-view {
  user-select: none;
  visibility: hidden;
  transition: opacity .4s;
  opacity: 0;
  display: inline-flex;
  background-color: var(--color-white);
  padding: 4px 8px;
  align-items: center;
  gap: 8px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  white-space: nowrap;
  box-shadow: 0 2px 7px 0 rgba(28, 45, 64, .12);
  
  & > span {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: 12px;
    font-weight: 700;
    color: var(--color-grey);
  }
}

.card__title {
  display: -webkit-box; /* Включаем поддержку многострочного текста */
  -webkit-line-clamp: 2; /* Ограничиваем текст до 2 строк */
  -webkit-box-orient: vertical; /* Устанавливаем направление блока на вертикальное */
  overflow: hidden; /* Прячем лишний текст */
  text-overflow: ellipsis; /* Добавляем многоточие */
}


</style>