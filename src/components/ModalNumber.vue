<template>
    <div v-if="isVisible" class="modalnumber">
        <h3>Numero estratto</h3>
        <p v-if="numeroEstratto">{{ numeroEstratto }}</p>
    </div>
    <div v-if="isVisible" class="velo"></div>
</template>


<script>
export default {
    props: {
        isVisible: Boolean,
        numeroEstratto: Number
    },

    data() {
        return {

        };
    },
    methods: {

    }
}
</script>

<style scoped>
.modalnumber {
    width: 65%;
    height: 75vh;
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