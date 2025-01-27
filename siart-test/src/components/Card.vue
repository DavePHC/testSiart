<script setup>
import IconQuickView from '@/components/icons/IconQuickView.vue'
import IconLike from '@/components/icons/IconLike.vue';
import IconCompare from '@/components/icons/IconCompare.vue';
import IconReview from '@/components/icons/IconReview.vue';
import IconToCard from '@/components/icons/IconToCard.vue'
import IconPlus from '@/components/icons/IconPlus.vue'
import IconMinus from '@/components/icons/IconMinus.vue'

defineProps({
  itemId: {
    type: Number
  },
  itemTitle: {
    type: String,
  },
  itemUrl: {
    type: String
  },
  itemPrice: {
    type: Number,
  },
  itemOldPrice: {
    type: Number,
  },
  itemNumber: {
    type: Number,
  },
  itemSticker: {
    type: String
  },
  isFavorite: {
    type: Boolean
  },
  isCompare: {
    type: Boolean
  }
})


</script>

<template>
  <article class="card">
    <div class="card__head">
      <button class="card__quick-view">
        <IconQuickView />
        <span>Быстрый просмотр</span>
      </button>
      <div class="card__favorite">
        <button class="button-icon button-icon_like">
          <IconCompare />
        </button>
        <button class="button-icon button-icon_compare">
          <IconLike />
        </button>
      </div>
      <span class="card__number">Арт: {{ itemNumber }}</span>
      <button class="card__review">
        <IconReview />
        5
      </button>
      <img class="card__image" :src="`images/${itemId}.png`" :alt="itemTitle">
    </div>
    <div class="card__body">
      <h3 class="card__title" :title="itemTitle">{{ itemTitle }}</h3>
      <div class="stickers">
        <span class="sticker sticker_in-stock">В наличии</span>
        <span class="sticker sticker_new">Новинка</span>
        <span class="sticker sticker_stock">Акция</span>
      </div>
      <div class="card__price">
        <div class="current-price">{{ itemPrice }} ₽ <span>шт.</span></div>
        <div class="old-price">{{ itemOldPrice }} ₽</div>
      </div>
      <div class="card__buttons">
        <button class="card-button card-button_order">Заказать</button>
        <button class="card-button card-button_in-card">
          <IconToCard />
          <span>В корзину</span>
        </button>
        <div class="card__counter">
          <button>
            <IconMinus />
          </button>
          <input type="text" name="counter" value="1">
          <button>
            <IconPlus />
          </button>
        </div>
      </div>
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
  box-shadow: 0 0 10px 0 rgba(28, 45, 64, .05);
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

  &>span {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: 12px;
    font-weight: 700;
    color: var(--color-grey);
  }
}

.card__favorite {
  position: absolute;
  display: flex;
  gap: 4px;
  top: 5px;
  right: 5px;
}

.button-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 28px;
  height: 28px;
  border-radius: 7px;
  background-color: var(--color-white);
  box-shadow: 0 2px 5px 0 rgba(28, 45, 64, .1);
}

.card__number {
  position: absolute;
  border-radius: 5px 5px 0 0;
  padding: 4px 6px;
  background-color: var(--color-white);
  left: 4px;
  bottom: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 12px;
  color: var(--color-text);
}

.card__review {
  position: absolute;
  border-radius: 5px 5px 0 0;
  display: flex;
  align-items: center;
  gap: 4px;
  padding: 4px;
  right: 4px;
  bottom: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 12px;
  color: var(--color-text);
}

.card__title {
  margin-top: 8px;
  line-height: 1.4em;
  min-height: 4.2em;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}

.card__price {
  margin-top: 12px;
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.current-price {
  font-size: 16px;
  line-height: 20px;
  font-weight: 600;
  order: 1;

  &>span {
    font-size: 14px;
    color: var(--color-grey);
  }
}

.old-price {
  font-size: 12px;
  line-height: 16px;
  color: var(--color-grey);
  text-decoration: line-through;
}

.stickers {
  margin-top: 12px;
  display: flex;
  gap: 4px;
}

.sticker {
  padding: 2px 4px;
  font-size: 8px;
  font-weight: 700;
  border-radius: 3px;
}

.sticker_in-stock {
  color: var(--color-green);
  background-color: var(--color-light-green);
}

.sticker_new {
  color: var(--color-white);
  background-color: var(--color-blue);
}

.sticker_stock {
  color: var(--color-white);
  background-color: var(--color-green);
}

.card__buttons {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-top: 12px;
}

.card-button {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  font-size: 14px;
  line-height: 20px;
  padding: 8px;
  color: var(--color-blue);
  border-radius: 8px;
  transition: .4s;
}

.card-button_order {
  outline: 1px solid var(--color-blue);
  background-color: var(--color-white);

  &:hover,
  &:focus-within {
    background-color: var(--color-light-grey);
  }

  &:active {
    background-color: var(--color-light-blue-active);
  }
}

.card-button_in-card {
  gap: 10px;
  background-color: var(--color-light-blue-default);

  &:hover,
  &:focus-within {
    background-color: var(--color-light-blue-hover);
  }

  &:active {
    background-color: var(--color-light-blue-active);
  }
}

.card__counter {
  display: grid;
  grid-template-columns: 36px 1fr 36px;
  gap: 4px;

  & button {
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 7px;
    border: 1px solid var(--color-light-grey);
    width: 36px;
    height: 36px;

    svg {
      width: 14px;
      height: 14px;
    }
  }

  & input {
    width: 100%;
    font-weight: 500;
    border-radius: 7px;
    border: 1px solid var(--color-light-grey);
    color: var(--color-black);
    text-align: center;
    transition: .4s;

    &:focus {
      outline: none;
      background-color: var(--color-light-blue-default);
      border: 1px solid var(--color-light-blue-default);
    }
  }
}


@media (min-width: 1400px) {

  .sticker {
    padding: 4px 8px;
    font-size: 10px;
  }

  .card__price {
    flex-direction: row;
    align-items: flex-end;
    gap: 12px;
  }

  .current-price {
    order: unset;
  }

}

@media (min-width: 1600px) {

  .current-price {
    font-size: 20px;
    line-height: 24px;
  }

  .old-price {
    font-size: 16px;
    line-height: 24px;
  }

  .card__counter button {
    width: 48px;
    height: 48px;
  }

  .card__counter {
    grid-template-columns: 48px 1fr 48px;
    gap: 8px;
  }

  .card__counter button svg {
    width: 18px;
    height: 18px;
  }

}
</style>