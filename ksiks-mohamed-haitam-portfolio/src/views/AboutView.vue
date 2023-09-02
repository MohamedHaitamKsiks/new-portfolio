<template>
    <div class="about-container">
        <h1 class="highlight"> About Me! </h1>
        <div class="about" :class="{'about-smaller': isScreenSmall}">
            <strong class="highlight"></strong>
            <p>
                Hello, I'm <strong class="highlight">Mohamed Haitam Ksiks</strong>, a passionate <strong class="highlight">game developer</strong> and dedicated <strong class="highlight">software engineering student</strong> at The <strong class="highlight">National school For Computer Science</strong>, located in <strong class="highlight">Morocco</strong>. 
            </p>

            <p>
                My journey into the captivating world of game development started as a labor of <strong class="highlight">love</strong>, and it has only grown stronger over the years. As a dedicated software engineering student, I've had the privilege of merging my academic knowledge with my lifelong passion, allowing me to create games that are not just <strong class="highlight">technologically robust</strong> but also deeply <strong class="highlight">immersive</strong>. 
            </p>

            <p>
                With a history of <strong class="highlight">freelance game development</strong>, a portfolio of <strong class="highlight">hobbyist</strong> projects, and active participation in thrilling <strong class="highlight">game jams</strong>, I bring a wealth of hands-on experience to the table.
            </p>

            <p>
                Together, let's embark on an exhilarating adventure where we turn dreams into interactive realities, and where pixels and code come together to craft unforgettable gaming experiences.
            </p>
        </div>
    </div>
</template>

<style scoped>
    .about-container
    {
        min-height: 100vh;

        display: flex;
        justify-content: center;
        align-items: flex-start;

        flex-direction: column;
    }

    .about
    {
        font-size: xx-large;
    }

    .about-smaller
    {
        font-size: x-large;
    }
</style>

<script>
export default
    {
        mounted() {
            window.addEventListener('resize', this.onWindowResize);
            this.onWindowResize();
        },
        unmounted() {
            window.removeEventListener('resize', this.onWindowResize);
        },
        data() {
            return {
                isScreenSmall: false,
            };
        },
        methods:
        {
            onWindowResize() {
                const thresholdWidth = 600;
                this.isScreenSmall = window.innerWidth < thresholdWidth;
            }
        }
    }
</script>