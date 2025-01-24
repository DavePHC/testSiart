<script setup>
import IconDoc from '@/components/icons/IconDoc.vue';
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
        <div class="form__layout">
          <div class="form__inputs">
            <input class="form__input" type="text" inputmode="text" placeholder="Имя*">
            <input class="form__input" type="tel" inputmode="tel" placeholder="Телефон*" required>
            <input class="form__input" type="email" inputmode="email" placeholder="E-mail*">
          </div>
          <textarea id="textArea" class="form__text-area" name="message" rows="3" placeholder="Ваш вопрос"></textarea>
        </div>
        <div class="form__footer">
          <button class="button-submit" type="submit">
            Задать вопрос
          </button>
          <div class="agreement-wrapper">
            <label class="agreement">
              <input id="hideCheckbox" class="hide-checkbox" type="checkbox">
              <span class="fake-checkbox"></span>
              Я согласен с условиями&nbsp;<a href="#" target="_blanck" rel="noopener">пользовательского
                соглашения.</a>
            </label>
          </div>
        </div>
      </form>
    </div>
  </section>

</template>

<style scoped lang="scss">
.section-form {
  padding: 4.2em 8.2em;
}

.form-wrapper {
  padding: 20px 32px;
  border: 1px solid var(--color-blue);
  border-radius: 24px;
}


.form-head {
  display: flex;
  gap: 20px;
  align-items: center;

  &__content {
    display: flex;
    flex-direction: column;
    gap: 4px;
  }

  h2 {
    font-size: 20px;
    font-weight: 500;
    color: var(--color-black);
  }

  p {
    color: var(--color-grey);
  }
}

.form {
  margin-top: 28px;
}

.form__inputs {
  display: flex;
  gap: 12px;
  justify-content: space-between;
}

.form__input,
.form__text-area {
  width: 100%;
  font-size: 16px;
  padding: 14px 16px;
  color: var(--color-text);
  background-color: var(--color-background-slider);
  border-radius: 12px;
  border: none;
  transition: .4s;

  &::placeholder {
    font-family: Inter, sans-serif;
    font-size: 16px;
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
  margin-top: 32px;
  resize: none;
}

.form__footer {
  display: flex;
  gap: 20px;
  align-items: center;
  margin-top: 16px;
}

.button-submit {
  display: flex;
  justify-content: center;
  align-items: center;
  max-width: 256px;
  line-height: 24px;
  width: 100%;
  font-size: 16px;
  padding: 14px;
  background-color: var(--color-blue);
  color: var(--color-white);
  border-radius: 12px;
  transition: .4s;

  &:hover {
    background-color: var(--color-blue-hover);
  }

  &:active {
    background-color: var(--color-blue-active);
  }
}

.agreement {
  position: relative;
  display: flex;
  align-items: center;
  font-size: 14px;
  color: var(--color-grey);
  cursor: pointer;

  a {
    text-decoration: underline;
    color: inherit;
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
  visibility: hidden;
}

.fake-checkbox {
  position: relative;
  display: inline-flex;
  width: 20px;
  height: 20px;
  border-radius: 4px;
  background-color: var(--color-light-blue-default);
  margin-right: 12px;

  &::before {
    content: '';
    opacity: 0;
    transition: .3s;
    display: inline-block;
    width: 10px;
    height: 10px;
    top: 50%;
    left: 50%;
    transform: translate(50%, 50%);
    background: url("data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTAiIGhlaWdodD0iMTAiIHZpZXdCb3g9IjAgMCAxMCAxMCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggZD0iTTguNzUgMi41TDQuMjQzNDIgNy41TDEuMjUgNC4zNzUiIHN0cm9rZT0iIzQwOTJGMSIgc3Ryb2tlLXdpZHRoPSIyIiBzdHJva2UtbGluZWNhcD0icm91bmQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiLz4KPC9zdmc+Cg==");
  }
}

.hide-checkbox:checked+.fake-checkbox::before {
  opacity: 1;
}
</style>