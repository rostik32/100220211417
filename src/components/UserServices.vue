<template>
  <div class="services">
    <table class="services__table">
      <thead>
        <tr>
          <th></th>
          <th class="text-center services__table-title">Услуг</th>
        </tr>
      </thead>

      <tbody class="services__table-body">
        <tr class="spacer"></tr>

        <tr v-for="service in services" :key="service.title">
          <td>
            <span class="services-title">{{ service.title }}</span>
            <div
              class="progress"
              :class="{ 'progress--high': getPercent(service.amount) > 30 }"
              :style="{ width: getPercent(service.amount) + '%' }"
            ></div>
          </td>
          <td class="text-center service-amount">{{ service.amount }}</td>
        </tr>

        <tr class="spacer"></tr>
      </tbody>

      <tfoot>
        <tr class="services__table-footer">
          <td>Всего</td>
          <td class="text-center">{{ total }}</td>
        </tr>
      </tfoot>
    </table>
  </div>
</template>

<script>
export default {
  name: 'UserServices',

  computed: {
    total() {
      const total = this.services.reduce((acc, item) => {
        acc += item.amount;
        return acc;
      }, 0);

      return total;
    },
  },

  methods: {
    getPercent(amount) {
      return (amount / this.total) * 100;
    },
  },

  data() {
    return {
      services: [
        {
          title: 'Ручное бронирование',
          amount: 11,
        },
        {
          title: 'Пакетные туры',
          amount: 3,
        },

        {
          title: 'Отели',
          amount: 1,
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.services {
  &__table {
    width: 100%;
    border-collapse: collapse;

    &-title {
      padding-bottom: 7px;
      font-size: 13px;
      line-height: 15px;
      font-weight: normal;
    }

    &-body {
      border-top: 1px solid #dadada;
      border-bottom: 1px solid #dadada;
    }

    &-footer {
      font-weight: bold;
      font-size: 16px;
      line-height: 26px;

      & td {
        padding: 15px 0;
      }
    }

    & td {
      position: relative;
      z-index: 10;
    }

    & .progress {
      position: absolute;
      left: 0;
      bottom: 1px;
      top: 1px;
      font-size: 13px;
      line-height: 26px;
      background: #ace2f8;
      border-radius: 0px 3px 3px 0px;
      border-left: 1px solid rgba(51, 51, 51, 0.2);
      padding-left: 6px;
      z-index: -1;

      &--high {
        background: #b1e19b;
      }
    }
  }
}

.spacer {
  height: 13px;
}

.service-title {
  display: inline-block;
  padding-left: 5px;
  font-size: 13px;
  line-height: 26px;
}

.service-amount {
  font-weight: bold;
  font-size: 13px;
  line-height: 15px;
}

.text-center {
  text-align: center;
}
</style>
