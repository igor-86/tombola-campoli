<template>
    <div class="img-cont">
        <img src="../assets/hero.jpg" alt="Image-hero">
    </div>
</template>

<script>
export default {
    name: "HeroImage"
}
</script>

<style scoped>
.img-cont {
    width: 100%;
    height: 300px;
}

.img-cont img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
}
</style>