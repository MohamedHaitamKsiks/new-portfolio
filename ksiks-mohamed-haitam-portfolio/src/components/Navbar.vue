<script setup>
import Navlink from './Navlink.vue';

</script>

<template>
    <nav class="" :class="{ 'nav-scrolled': isScrolled }">
        <div class="links-list">

            <Navlink href="/" text="Home" :isTextVisible="!isScreenSmall">
                <i class="link-icon bi bi-house"></i>
            </Navlink>
    
            <Navlink href="/about" text="About" :isTextVisible="!isScreenSmall">
                <i class="link-icon bi bi-person"></i>
            </Navlink>

            <Navlink href="/skills" text="Skills" :isTextVisible="!isScreenSmall">
                <i class="link-icon bi bi-tools"></i>
            </Navlink>
    
            <Navlink href="/projects" text="Projects" :isTextVisible="!isScreenSmall">
                <i class="link-icon bi bi-code-slash"></i>
            </Navlink>
    
            <Navlink href="Resume.pdf" :isFile="true" text="Resume" :isTextVisible="!isScreenSmall">
                <i class="link-icon bi bi-file-earmark-text"></i>
            </Navlink>

        </div>
    </nav>
</template>

<style scoped>
    nav
    {
        height:80px;
        margin: 0px;

        position: fixed;
        left: 0px;
        right: 0px;

        display: flex;
        align-items: center;
        justify-content: center;

        transition: background-color 0.2s;

        z-index: 100;
    }

    .nav-scrolled
    {
        background-color: #2a2550c0;
        box-shadow: 0px 4px 16px 4px rgba(0, 0, 0, 0.042);
    }

    .links-list
    {
        width: 100%;
        max-width: 800px;

        display: flex;
        align-items: center;
        justify-content: center;
    }

    .link-icon
    {
        font-size: 32px;
    }

</style>

<script>
    export default
    {
        mounted()
        {
            window.addEventListener('scroll', this.onWindowScroll);
            window.addEventListener('resize', this.onWindowResize);

            this.onWindowScroll();
            this.onWindowResize();
        },
        unmounted()
        {
            window.removeEventListener('scroll', this.onWindowScroll);
            window.removeEventListener('resize', this.onWindowResize);
        },
        data()
        {
            return {
                isScrolled: false,
                isScreenSmall: false,
            };
        },
        methods:
        {
            onWindowScroll()
            {
                const scrollY = window.scrollY;
                const thresholdScroll = 64;

                this.isScrolled = scrollY > thresholdScroll;
            },
            onWindowResize()
            {
                const thresholdWidth = 670;
                this.isScreenSmall = window.innerWidth < thresholdWidth;
            }
        }
    }
</script>