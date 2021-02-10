<template>
  <form @keydown.ctrl.enter="onSubmit" @submit.prevent="onSubmit" class="form">
    <textarea class="form__message" v-model="message"></textarea>

    <button type="submit" class="form__submit">Написать консультанту</button>
  </form>
</template>

<script>
export default {
  name: 'MessageForm',
  data() {
    return {
      message: '',
    };
  },

  methods: {
    onSubmit() {
      const review = {
        username: 'Вы',
        timestamp: Date.now(),
        text: this.message,
      };

      this.$emit('submit', review);
      this.message = '';
    },
  },
};
</script>

<style lang="scss">
.form {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 28px 21px 34px 21px;
  background-color: #f2f2f2;

  &__message {
    width: 100%;
    height: 63px;
    resize: none;
    background-color: #fff;
    border: 1px solid #000000;
    border-radius: 1px;
    margin-bottom: 23px;
  }

  &__submit {
    display: inline-block;
    padding: 12px 0;
    min-width: 280px;
    font-weight: bold;
    font-size: 16px;
    line-height: 21px;
    background-color: #fdd639;
    border-radius: 23px;
    border: none;
    color: #333333;
    cursor: pointer;
  }
}
</style>
