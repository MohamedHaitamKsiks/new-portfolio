<script setup>
import { RouterView } from 'vue-router';
import Navbar from './components/Navbar.vue';
import FooterContainer from './components/FooterContainer.vue';
</script>

<template>
    <header>
        <Navbar/>
	</header>

    <div class="router-view-container">
        <div class="router-view"> <RouterView /> </div>
    </div>

    <footer>
        <FooterContainer/>
    </footer>
</template>

<style scoped>
    .router-view-container
    {
        display: flex;
        justify-content: center;
    }

    .router-view
    {
        width: 100%;
        max-width: 1280px;

        padding: 16px;
        margin-top: 64px;
        margin-bottom: 64px;
    }
</style>