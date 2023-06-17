<template>
  <div class="page-container">
    <Navbar :logo="logo_src" :alt="app_name" />
    <RouterView class="content"/>
    <Footer />
  </div>
</template>

<script>
  import { RouterLink, RouterView } from 'vue-router'
  import Navbar from './components/Navbar.vue';
  import Footer from './components/Footer.vue';

  export default {
    components: {
      Navbar,
      Footer,
    },
    data() {
      return {
        logo_src: "./img/logo.png",
        app_name: "Make Your Burguer"
      }
    }
  }
</script>


<style>

.content {
        padding-bottom: 2.5rem;
    }

  * {
    font-family: Helvetica;
    padding: 0;
    margin: 0;
  }

  main-container {
    margin: 50px;
    min-height: 250px;
  }

  h1 {
    text-align: center;
    font-size: 42px;
    margin-block: 30px;
    color: #222;
  }

  .page-container {
  position: relative;
  min-height: 100vh;
}
</style>
