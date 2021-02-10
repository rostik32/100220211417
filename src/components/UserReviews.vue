<template>
  <div class="reviews">
    <div class="reviews__header">
      <div class="reviews__header-col">
        <span class="reviews__header-title">Последние отзывы</span>

        <a href="#" class="reviews__header-link">Все отзывы</a>
      </div>

      <div class="reviews__header-meta">
        <div class="reviews__header-counter">
          <img src="@/assets/icons/like.png" alt="like icon" />
          <span>131</span>
        </div>

        <div class="reviews__header-counter">
          <img src="@/assets/icons/comment.png" alt="like icon" />
          <span>14</span>
        </div>
      </div>
    </div>

    <ul class="reviews__list">
      <li
        class="reviews__item"
        v-for="review in reviews"
        :key="review.timestamp"
      >
        <p class="reviews__item-header">
          <span class="reviews__item-user">{{ review.username }}</span>
          <span class="reviews__item-time">
            {{ review.timestamp | getDate }}
          </span>
        </p>

        <p
          class="reviews__item-text"
          :class="{
            'reviews__item-text--current-user': review.username === 'Вы',
          }"
        >
          {{ review.text }}
          <span class="reviews__item-triangle"></span>
        </p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'UserReviews',
  props: ['reviews'],

  filters: {
    getDate: function (value) {
      if (!value) return '';
      const date = new Date(+value);

      const formatter = new Intl.DateTimeFormat('ru', {
        year: 'numeric',
        day: 'numeric',
        month: 'long',
      });

      return formatter.format(date);
    },
  },
};
</script>

<style lang="scss">
.reviews {
  padding: 0 20px;

  &__header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 11px;

    &-title {
      font-weight: bold;
      font-size: 16px;
      line-height: 16px;
      margin-right: 5px;
    }

    &-link {
      line-height: 16px;
      color: #005da1;
    }

    &-col {
      display: flex;
      align-items: center;
      flex-wrap: wrap;

      &:first-child {
        margin-right: 10px;
      }
    }

    &-meta {
      display: flex;
      align-self: flex-start;
      align-items: center;
    }

    &-counter {
      display: flex;
      align-items: center;

      &:first-child {
        margin-right: 15px;
      }

      & img {
        margin-right: 3px;
      }
    }
  }

  &__list {
    margin: 0;
    padding: 0;
    padding-bottom: 6px;
    list-style: none;
  }

  &__item {
    padding-bottom: 16px;

    &-header {
      margin: 0;
      margin-bottom: 15px;
    }

    &-user {
      line-height: 19px;
      font-weight: 700;
      margin-right: 5px;
    }

    &-time {
      color: #808080;
      font-size: 12px;
    }

    &-triangle {
      width: 0;
      height: 0;
      display: block;
      position: absolute;
      top: -15px;
      left: 20px;
      border-bottom: 15px solid #f2fbff;
      border-right: 15px solid transparent;

      &::before {
        content: '';
        width: 20px;
        display: block;
        position: absolute;
        top: 7px;
        left: -2px;
        border-top: 1px solid #c4cbcf;
        transform: rotate(45deg);
      }

      &::after {
        content: '';
        width: 15px;
        display: block;
        position: absolute;
        top: 7px;
        left: -7px;
        border-top: 1px solid #c4cbcf;
        transform: rotate(90deg);
      }
    }

    &-text {
      position: relative;
      margin: 0;
      padding: 20px;
      background-color: #f2fbff;
      border: 1px solid #c4cbcf;
      box-sizing: border-box;
      box-shadow: 0px 4px 10px rgba(128, 128, 128, 0.1);
      word-break: break-all;

      &--current-user {
        background-color: #e1fde3;

        & .reviews__item-triangle {
          border-bottom-color: #e1fde3;
        }
      }
    }
  }
}
</style>
