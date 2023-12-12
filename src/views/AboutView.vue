<!-- TabelloneTombola.vue -->
<template>
  <div>
    <ModalNumber :isVisible="mostraModalNumero" :numeroEstratto="numeroCasuale" />
    <ModalPartitaFinita :isVisible="mostraModalPartitaFinita" :numeroEstratto="numeroCasuale"
      @resetta-partita="resettaPartita" />
    <ModalFinePartita :isVisible="mostraResettaPartita" @resetta-partita="resettaPartita" />
  </div>
  <div class="area">
    <div class="titolo">
      <h1>Tabellone Tombola</h1>
    </div>
    <div class="gioco">
      <div class="row" v-for="(row, rowIndex) in tabellone" :key="rowIndex">
        <div class="numero" v-for="(numero, columnIndex) in row" :key="columnIndex"
          :class="{ 'estratto': numeriEstratti.includes(numero) && !mostraModalNumero }">
          <p :class="{ 'bianco': numeriEstratti.includes(numero) && !mostraModalNumero }">
            {{ numero }}
          </p>
        </div>
      </div>
    </div>
    <div class="game">
      <button v-if="!nuovaPartita" id="newgame" @click="avviaPartita">Nuova partita</button>
      <button v-if="nuovaPartita" id="endgame" @click="partitaReset">Fine partita</button>
      <div v-if="nuovaPartita" class="newgame">
        <button id="estract" @click="estraiNumero">Estrai numero</button>
        <div class="form" v-for="(premio, index) in listaPremi" :key="index">
          <label :for="premio.label">{{ premio.label }}</label>
          <input type="checkbox" :name="premio.label" :id="premio.label" v-model="premio.stato">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ModalNumber from '@/components/ModalNumber.vue';
import ModalPartitaFinita from '@/components/ModalPartitaFinita.vue';
import ModalFinePartita from '@/components/ModalFinePartita.vue';
export default {
  components: {
    ModalNumber,
    ModalPartitaFinita,
    ModalFinePartita
  },
  data() {
    return {
      tabellone: this.generaTabellone(),
      nuovaPartita: false,
      listaPremi: [
        { label: "Ambo", stato: false },
        { label: "Terno", stato: false },
        { label: "Quaterna", stato: false },
        { label: "Cinquina", stato: false },
        { label: "Tombola", stato: false },
        { label: "Tombolino", stato: false },

      ],
      mostraModalNumero: false,
      mostraModalPartitaFinita: false,
      mostraResettaPartita: false,
      numeroCasuale: null,
      numeriEstratti: []
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
    },
    avviaPartita() {
      this.nuovaPartita = true;
      this.bottonStart = false;
    },
    /* estraiNumero() {
      const numeroCasuale = Math.floor(Math.random() * 90) + 1;
      this.numeroEstratto = numeroCasuale;
      this.mostraModal = true;

      setTimeout(() => {
        this.mostraModal = false;
      }, 3000);
    } */
    estraiNumero() {
      if (this.partitaFinita) {
        return;
      }

      // Logica per estrarre un numero casuale che non è stato ancora estratto
      do {
        this.numeroCasuale = Math.floor(Math.random() * 90) + 1;
      } while (this.numeriEstratti.includes(this.numeroCasuale));

      // Aggiungi il numero estratto all'array
      this.numeriEstratti.push(this.numeroCasuale);
      console.log(this.numeriEstratti);

      // Passa il numero estratto come prop a ModalNumber
      this.mostraModalNumero = true;

      // Verifica se tutti i numeri sono stati estratti
      const tuttiNumeriEstratti = this.numeriEstratti.length === 90;

      if (tuttiNumeriEstratti) {
        // Se tutti i numeri sono stati estratti, mostra il modale di fine partita
        this.mostraModalPartitaFinita = true;
        // Imposta la variabile partitaFinita a true (se necessario)
        this.partitaFinita = true;
      }

      setTimeout(() => {
        this.mostraModalNumero = false;
      }, 3000);
    },
    partitaReset() {
      this.mostraResettaPartita = true;
    },
    resettaPartita() {
      // Resetta tutte le variabili per iniziare una nuova partita
      this.mostraModalNumero = false;
      this.mostraModalPartitaFinita = false;
      this.numeroCasuale = null;
      this.numeriEstratti = [];
      this.partitaFinita = false;
      this.mostraResettaPartita = false;
      this.nuovaPartita = false;
    }
  }
};
</script>

<style scoped>
.gioco {
  width: 60%;
  height: 70vh;
  margin: 1rem auto;
  padding: 1rem 0;
}

.titolo {
  position: absolute;
  right: 40px;
  top: 40px;
  padding: 1rem;
  background-color: white;
  border-radius: .9rem 0 .9rem 0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1), 0 4px 8px rgba(0, 0, 0, 0.1);
  transform: rotate(-7deg);
  display: flex;
  align-items: center;
  justify-content: center;
}

.titolo h1 {
  font-size: 1.4rem;
  color: #A63F03;
}

.row {
  display: flex;
  width: 100%;
  height: calc(100% / 10);

}

.row:nth-child(4) {
  margin-bottom: 0.8rem;
}

.row:nth-child(7) {
  margin-bottom: 0.8rem;
}

.numero {
  width: calc(100% / 10);
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid #A63F03;
  padding: 10px;
  text-align: center;
  color: #A63F03;
  margin-right: .4rem;
  margin-bottom: .7rem;
}

.numero.estratto {
  background-color: #A63F03;
}

.numero.estratto p.bianco {
  color: white;
}

.numero:nth-child(6) {
  margin-left: 0.8rem;
}

.numero:nth-child(1) {
  margin-left: 0.4rem;
}

.game {
  width: 90%;
  padding: 1rem 0;
  margin: 0 auto;
  border: 1px solid #A63F03;
  display: flex;
  justify-content: space-around;
}

.newgame {
  width: 80%;
  display: flex;
  justify-content: space-between;
}

.newgame button {
  margin-right: 1rem;
}

.form {
  width: 40%;
  display: flex;
  align-items: center;
  justify-content: space-around;
}

.game button {
  padding: .7rem 1.2rem;
  background-color: #A63F03;
  color: white;
  border-radius: .3rem;
  border: none;
  font-size: 0.7rem;
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

