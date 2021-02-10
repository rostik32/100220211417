<template>
  <div id="app">
    <div class="container">
      <user-info></user-info>

      <user-reviews :reviews="reviews"></user-reviews>

      <message-form @submit="addReview"></message-form>
    </div>
  </div>
</template>

<script>
import UserInfo from './components/UserInfo';
import UserReviews from './components/UserReviews';
import MessageForm from './components/MessageForm';

export default {
  name: 'App',

  components: { UserInfo, UserReviews, MessageForm },

  data() {
    return {
      reviews: [
        {
          username: 'Самуил',
          timestamp: '1315930606',
          text: 'Привет, Верунь! ниче себе ты крутая. фотка класс!!!! ',
        },

        {
          username: 'Лилия Семёновна',
          timestamp: '1316017006',
          text:
            'Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент, это и есть всемирно известный центр огранки алмазов и торговли бриллиантами?',
        },

        {
          username: 'Лилия Семёновна',
          timestamp: '1316017032',
          text:
            'Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент?',
        },
      ],
    };
  },

  methods: {
    addReview(review) {
      this.reviews.push(review);
    },
  },
};
</script>

<style lang="scss">
body {
  margin: 0;
  font-family: Arial, sans-serif;
  font-size: 14px;
  line-height: 20px;
  color: #333333;
  background-color: #e5e5e5;
}

.container {
  margin: 0 auto;
  max-width: 720px;
  background-color: #fff;
}
</style>
