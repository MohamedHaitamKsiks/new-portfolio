
<template>
    <div class="footer-container">
        <div class="footer-socials">
            <a href="https://www.linkedin.com/in/mohamed-haitam-ksiks-58a56921a/" class="bi bi-linkedin"> </a>
            <a href="https://github.com/MohamedHaitamKsiks" class="bi bi-github"> </a>
            <a href="https://simple-team.itch.io/" class="social-icon itch-icon"> </a>
            <a href="https://www.fiverr.com/haitamksiks?public_mode=true" class="social-icon fiverr-icon"> </a>
        </div>
    </div>
</template>

<style scoped>
    .footer-container
    {
        padding: 16px;

        display: flex;
        justify-content: center;
        align-items: center;

        background-color: rgba(0, 0, 0, 0.276);

    }
    .footer-socials
    {
        flex: 1;
        font-size: 30px;
        width: 100%;
        max-width: 800px;

        display: flex;
        justify-content: space-evenly;
        align-items: center;
    }

    .social-icon
    {
        background-size:contain;
        background-repeat: no-repeat;
        background-position: center;

        width: 32px;
        height: 32px;
    }

    .itch-icon
    {
        background-image: url('../assets/icons/itch.svg');
    }

    .fiverr-icon
    {
        background-image: url('../assets/icons/fiverr.svg');
    }

    .footer-socials a
    {
        color: white;
        text-decoration: none;
        display: flex;
    }
</style>