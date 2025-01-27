<script setup>


import { ref } from 'vue';

import IconDoc from '@/components/icons/IconDoc.vue';
import IconClose from '@/components/icons/IconClose.vue';
import IconSmile from '@/components/icons/IconSmile.vue';


const dialog = ref(null);

const openDialog = () => {
  if (dialog.value) {
    dialog.value.showModal();
  }
};

const closeDialog = () => {
  if (dialog.value) {
    dialog.value.close();
  }
};

</script>

<template>
  <section class="section-form">
    <div class="form-wrapper">
      <div class="form-head">
        <IconDoc />
        <div class="form-head__content">
          <h2>
            Не нашли ответа на свой вопрос?
          </h2>
          <p>
            Напишите нам, и мы предоставим необходимую информацию.
          </p>
        </div>
      </div>
      <form class="form" action="#">
        <div class="form__content">
          <input class="form__input" type="text" inputmode="text" placeholder="Имя*">
          <input class="form__input" type="tel" inputmode="tel" placeholder="Телефон*" required>
          <input class="form__input" type="email" inputmode="email" placeholder="E-mail*">
          <textarea id="textArea" class="form__text-area" name="message" rows="3" placeholder="Ваш вопрос"></textarea>
        </div>
        <div class="form__footer">
          <button @click.prevent="openDialog" class="button-submit" type="submit">
            Задать вопрос
          </button>
          <div class="agreement-wrapper">
            <label class="agreement">
              <input id="hideCheckbox" class="hide-checkbox" type="checkbox">
              <span class="fake-checkbox"></span>
              Я согласен с условиями <a href="#" target="_blanck" rel="noopener">пользовательского соглашения.</a>
            </label>
          </div>
        </div>
      </form>
    </div>
    <dialog ref="dialog" id="modalSuccess" class="modal-wrapper" aria-label="Благодарность за фидбек">
      <div class="overlay">
        <form class="modal">
          <button @click.prevent="closeDialog" class="modal__close">
            <IconClose />
          </button>
          <IconSmile />
          <h3 class="modal__title">
            Спасибо
          </h3>
          <p class="modal__text">
            Вопрос отправлен
          </p>
          <button @click.prevent="closeDialog" class="modal__button">
            Хорошо :)
          </button>
        </form>
      </div>
    </dialog>
  </section>
</template>

<style scoped lang="scss">
.section-form {
  padding: 24px 20px;
}

.form-wrapper {
  padding: 16px;
  border: 1px solid var(--color-blue);
  border-radius: 24px;
}

.form-head {
  display: flex;
  gap: 14px;

  &__content {
    display: flex;
    flex-direction: column;
  }

  h2 {
    font-weight: 500;
    line-height: 20px;
    color: var(--color-black);
  }

  p {
    line-height: 20px;
    color: var(--color-grey);
  }
}

.form {
  margin-top: 28px;
}

.form__content {
  display: grid;
  gap: 8px;
}

.form__input,
.form__text-area {
  padding: 12px 16px;
  width: 100%;
  font-size: inherit;
  line-height: 20px;
  color: var(--color-text);
  background-color: var(--color-background-slider);
  border-radius: 12px;
  border: none;
  transition: .4s;

  &::placeholder {
    font-family: Inter, sans-serif;
    font-size: inherit;
    font-weight: 400;
    color: var(--color-grey);
  }

  &:invalid {
    background-color: var(--color-red-invalid);
  }

  &:hover {
    background-color: var(--color-input-hover);
  }

  &:focus {
    outline: none;
    background-color: var(--color-background-slider);
  }
}

.form__text-area {
  resize: none;
}

.form__footer {
  margin-top: 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.button-submit {
  padding: 8px;
  width: 100%;
  max-width: var(--max-width-submit-button);
  display: flex;
  justify-content: center;
  align-items: center;
  line-height: var(--base-text-line-height);
  background-color: var(--color-blue);
  color: var(--color-white);
  border-radius: 8px;
  transition: .4s;
  -webkit-tap-highlight-color: transparent;

  &:hover {
    background-color: var(--color-blue-hover);
  }

  &:active {
    background-color: var(--color-blue-active);
  }
}

// Agreement Checkbox

.agreement-wrapper {
  text-align: center;
}

.agreement {
  padding-left: 32px;
  position: relative;
  color: var(--color-grey);
  cursor: pointer;
  -webkit-tap-highlight-color: transparent;

  a {
    color: inherit;
    font-weight: 500;
    text-decoration: underline;
  }
}

.hide-checkbox {
  position: absolute;
  width: 0;
  height: 0;
  top: 0;
  left: 0;
  z-index: -1;
  appearance: none;
  -webkit-appearance: none;
}

.fake-checkbox {
  position: absolute;
  margin-left: -32px;
  width: 20px;
  height: 20px;
  background-image: url(../../public/images/checkbox/checkbox-default.svg);
  background-size: cover;
}

.hide-checkbox:checked+.fake-checkbox {
  background-image: url(../../public/images/checkbox/checkbox-checked.svg);
}

.hide-checkbox:focus+.fake-checkbox {
  background-image: url(../../public/images/checkbox/checkbox-focus.svg);
}

.hide-checkbox:checked:focus+.fake-checkbox {
  background-image: url(../../public/images/checkbox/checkbox-focus-checked.svg);
}

// END Agreement Checkbox

// Modal

.modal-wrapper {
  padding: 0;
  border: none;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 10;
  max-width: unset;
  width: 100%;
  min-height: 100vh;
}

.modal {
  padding: 72px 28px 28px 28px;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 16px;
  width: 100%;
  min-height: 100vh;
  background-color: var(--color-white);

  &__title {
    font-weight: 500;
    font-size: 14px;
    line-height: 24px;
  }

  &__text {
    font-size: 12px;
    line-height: 20px;
    color: var(--color-grey);
  }

  &__button {
    padding: 8px;
    font-size: 14px;
    line-height: 20px;
    color: var(--color-blue);
    background-color: var(--color-light-blue-default);
    border-radius: 8px;
    width: 100%;
    max-width: var(--max-width-submit-button);
  }
}

.modal__close {
  position: absolute;
  top: 28px;
  right: 28px;
  display: flex;
  width: 28px;
  height: 28px;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background-color: var(--color-light-blue-default);
  transition: .4s;

  &:hover,
  &:focus-within {
    background-color: var(--color-light-blue-hover);
    box-shadow: 0 0 7px 0 rgba(28, 45, 64, .12);
  }

  &:active {
    background-color: var(--color-light-blue-active);
    box-shadow: 0 0 7px 0 rgba(28, 45, 64, .1);
  }
}

// END Modal



// Media Queries

@media (min-width: 578px) {

  .section-form {
    padding: 24px 56px;
  }

  .agreement-wrapper {
    text-align: left;
  }

  .modal__title {
    font-size: 16px;
  }

}

@media (min-width: 768px) {

  .section-form {
    padding: 48px 36px;
  }

  .form-head h2 {
    font-size: 16px;
  }

  .form__content {
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
  }

  .form__text-area {
    grid-column: 1 / -1;
  }

  .form__footer {
    flex-direction: row;
  }

  .modal-wrapper {
    background-color: rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(5px);
  }

  .overlay {
    width: 100%;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .modal {
    padding: 28px;
    max-width: 422px;
    min-height: unset;
    height: auto;
    border-radius: 24px;
  }

  .modal__close {
    top: 0;
    right: -40px;
  }

}

@media (min-width: 1025px) {

  .form-wrapper {
    padding: 16px 24px;
  }

  .section-form {
    padding: 48px 108px;
  }

}

@media (min-width: 1600px) {

  .section-form {
    padding: 68px 130px;
  }

  .form-head h2 {
    font-size: 20px;
    line-height: 28px;
  }

  .form-head p {
    line-height: 24px;
  }

  .form__input,
  .form__text-area {
    padding: 14px 16px;
  }

  .button-submit {
    padding: 14px;
  }

}

// END Media Queries</style>