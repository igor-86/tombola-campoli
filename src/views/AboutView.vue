<!-- TabelloneTombola.vue -->
<template>
  <div>
    <h1>Tabellone Tombola</h1>
    <div class="row" v-for="(row, rowIndex) in tabellone" :key="rowIndex">
      <div class="numero" v-for="(numero, columnIndex) in row" :key="columnIndex">
        {{ numero }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tabellone: this.generaTabellone()
    };
  },
  methods: {
    generaTabellone() {
      const numeri = Array.from({ length: 90 }, (_, index) => index + 1);
      const tabellone = [];

      for (let i = 0; i < 9; i++) {
        const row = numeri.slice(i * 10, (i + 1) * 10);
        tabellone.push(row);
      }

      return tabellone;
    }
  }
};
</script>

<style scoped>
.row {
  display: flex;
  width: 60%;
  height: 10%;
  margin: 0 auto;
}

.numero {
  width: calc(100% / 10);
  height: calc(100% / 9);
  border: 1px solid #A63F03;
  padding: 10px;
  text-align: center;
  color: #A63F03;
  margin-right: .7rem;
  margin-bottom: .7rem;
}
</style>

