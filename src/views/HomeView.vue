<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <WelcomePage msg="Benvenuto sul sito di Natale" />
  </div>
</template>

<script>
// @ is an alias to /src
import WelcomePage from '@/components/WelcomePage.vue';
export default {
  name: 'HomeView',
  components: {
    WelcomePage
  }
}
</script>
