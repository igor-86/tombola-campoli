<!-- TabelloneTombola.vue -->
<template>
  <div class="gioco">
    <h1>Tabellone Tombola</h1>
    <div class="row" v-for="(row, rowIndex) in tabellone" :key="rowIndex">
      <div class="numero" v-for="(numero, columnIndex) in row" :key="columnIndex">
        {{ numero }}
      </div>
    </div>
    <button>Nuova partita</button>
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
.gioco {
  width: 60%;
  margin: 0 auto;
  padding: 2rem 0;
}

h1 {
  font-size: 1.2rem;
  margin-bottom: 1.7rem;
}

.row {
  display: flex;
  width: 100%;


}

.row:nth-child(4) {
  margin-bottom: 0.8rem;
}

.row:nth-child(7) {
  margin-bottom: 0.8rem;
}

.numero {
  width: calc(100% / 10);
  height: calc(100% / 10);
  border: 1px solid #A63F03;
  padding: 10px;
  text-align: center;
  color: #A63F03;
  margin-right: .7rem;
  margin-bottom: .7rem;
}

.numero:nth-child(6) {
  margin-left: 0.8rem;
}

button {
  margin-top: 2rem;
  padding: 1rem 1.4rem;
  background-color: #A63F03;
  color: white;
  border-radius: .3rem;
  border: none;
  font-size: 0.8rem;
  text-transform: uppercase;
  font-weight: 700;
  transition: .2s ease-in;
}

button:hover {
  transform: scale(1.1);
  background-color: #a63f03;
  cursor: pointer;
}
</style>

