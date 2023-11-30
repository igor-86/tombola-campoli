<template>
    <HeroImage />
    <div class="container-hero">
        <div class="card">
            <h1>{{ msg }}</h1>
        </div>
    </div>
</template>

<script>
import HeroImage from './HeroImage.vue';
export default {
    name: "WelcomePage",
    components: {
        HeroImage
    },
    props: {
        msg: String
    }
}
</script>
<style scoped>
.container-hero {
    position: relative;
}

.card {
    width: 50%;
    height: 400px;
    background-color: #ac5e31;
    border-radius: .735rem;
    position: absolute;
    top: -30px;
    left: 50%;
    transform: translateX(-50%);
}

.card h1 {
    color: white;
    text-align: center;
}
</style>