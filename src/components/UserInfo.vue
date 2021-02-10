<template>
  <div class="user">
    <div class="user__avatar-outer">
      <img
        src="@/assets/user/avatar.jpg"
        alt="Вероника Ростова"
        width="124"
        height="124"
        class="user__avatar"
      />
    </div>

    <div class="user__info">
      <span class="user__name"> Вероника Ростова </span>
      <span class="user__profession"> Менеджер по продажам </span>

      <p class="user__description">
        Подберу для вас самые лучшие предложения. Мои услуги абсолютно бесплатны
      </p>

      <user-services></user-services>
    </div>
  </div>
</template>

<script>
import UserServices from './UserServices';

export default {
  name: 'UserInfo',
  components: {
    UserServices,
  },
};
</script>

<style lang="scss">
.user {
  display: flex;
  align-items: flex-start;
  padding: 14px 19px 0 17px;
  margin-bottom: 6px;

  &__info {
    display: flex;
    flex-direction: column;
  }

  &__avatar-outer {
    flex-shrink: 0;
    margin-right: 10px;
    border-radius: 50%;
    overflow: hidden;
    line-height: 0;
    z-index: 10;

    @media (max-width: 400px) {
      width: 100px;
      height: 100px;
    }
  }

  &__avatar {
    max-width: 100%;
    object-fit: cover;
  }

  &__name {
    font-weight: bold;
    font-size: 16px;
    margin-top: 6px;
    margin-bottom: 2px;
  }

  &__profession {
    margin-bottom: 5px;
    color: #808080;
    font-size: 12px;
  }

  &__description {
    padding: 10px 10px 10px 45px;
    margin: 0;
    margin-left: -45px;
    margin-bottom: 13px;
    border: 1px solid #dadada;
    border-radius: 5px;
    background: #fffbc8;
    word-break: break-all;
  }
}
</style>
