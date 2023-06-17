<template>
  <div class="main-container">
    <Banner />
    <h1>Monte o seu burger:</h1>
    <BurgeForm />
  </div>
</template>


<script>
  import Banner from '../components/Banner.vue';
  import BurgeForm from '../components/BurgeForm.vue';

  export default {
    Name: 'Home',
    components: {
      Banner,
      BurgeForm,
    },

  }

</script>

<style scoped>

</style>
