<template>
    <footer id="footer">
        <p>Make your Burger &copy; 2023</p>
    </footer>
</template>

<script>
    export default {
        name: 'Footer'
    }

</script>

<style scoped>
    #footer {
        height: 500px;
        background-color: #222;
        border-top: 2px solid #111;
        color: #FCBA03;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        bottom: 0;
        position: absolute;
        width: 100%;
        height: 2.5rem;
    }
</style>