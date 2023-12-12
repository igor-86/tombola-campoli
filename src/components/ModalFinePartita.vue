<template>
    <div v-if="isVisible" class="modalFinish">
        <h3>Sei sicuro di voler concludere la partita?</h3>

        <button @click="resettaPartita">Resetta</button>
    </div>
    <div v-if="isVisible" class="velo"></div>
</template>


<script>
export default {
    props: {
        isVisible: Boolean
    },
    emits: ['resetta-partita'],
    data() {
        return {

        };
    },
    methods: {
        resettaPartita() {
            this.$emit('resetta-partita');
        }
    }
}
</script>

<style scoped>
.modalFinish {
    width: 50%;
    height: 40vh;
    background-color: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1), 0 4px 8px rgba(0, 0, 0, 0.1);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 10;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.modalFinish h3 {
    margin-bottom: 2rem;
}

.velo {
    width: 100%;
    height: 100vh;
    position: absolute;
    background-color: #A63F03;
    opacity: 0.63;
    top: 0;
    left: 0%;
    z-index: 5;
}
</style>