<template>
    <nav class="navbar navbar-expand-lg navbar-dark">
        <div class="container-fluid">
            <RouterLink to="/" class="navbar-brand" id="logo-url">
                <img :src="logo" :alt="alt" id="logo">
            </RouterLink>
            <button class="navbar-toggler  " type="button" data-bs-toggle="collapse" data-bs-target="#navbarText" aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarText">
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li class="nav-item">
                    <RouterLink to="/" class="nav-link ">Home</RouterLink>
                </li>
                <li class="nav-item">
                    <RouterLink to="/Pedidos" class="nav-link ">Pedidos</RouterLink>
                </li>
            </ul>
            </div>
        </div>
    </nav>
</template>

<script>
    export default {
        name: 'Navbar',
        props: ["logo", "alt"]
    }

</script>

<style scoped>
    #logo {
        width: 40px;
        height: 40px;
    }

    nav {
        background-color: #222;
        border-bottom: 2px solid #111;
    }

    nav a {
        color: #FCBA03;
        transition: .5s;
    }

    nav a:hover {
        color: white;
    }

    nav a:focus {
        color: white;
    }
</style>