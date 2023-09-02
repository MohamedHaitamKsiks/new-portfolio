<script setup>
import ProjectsContainer from '../components/ProjectsContainer.vue';
import projects from '../assets/projects/projects.json'
</script>

<template>
    
    <div class="projects-container">
        
        <h1 class="highlight"> My Projects </h1>

        <div class="projects-list">
            <ProjectsContainer v-for="project in projects" 
            :id="project.id"
            :title="project.title"
            :images="project.images"
            :main="project.main"
            :tools="project.tools"
            :description="project.description"
            :link="project.link"
            :isScreenSmall="isScreenSmall"/>
        </div>
    </div>

</template>

<style scoped>
    .projects-container
    {
        margin-top: 80px;
        min-height: 100vh;

        display: flex;
        flex-direction: column;
        justify-content: start;
        align-items: center;
    }

    .projects-container h1
    {
        text-align: center;
    }

    .projects-list 
    {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        width: 100%;
        max-width: 1000px;
        gap: 16px;

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
                const thresholdWidth = 900;
                this.isScreenSmall = window.innerWidth < thresholdWidth;
            }
        }
    }
</script>