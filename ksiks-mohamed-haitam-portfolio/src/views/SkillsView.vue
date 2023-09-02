<script setup>
import skills from '../assets/skills.json';
import SkillContainer from '../components/SkillContainer.vue';
</script>

<template>
    <div class="skills-container">

        <div v-for="skillCollection, category in skills" 
        class="skills-collection">
            <h2 :class="'highlight ' + skillCollection.icon"> &nbsp; {{ category }} </h2>
            <div class="skills-list" :class="{'skills-list-smaller': isScreenSmall}">
                <SkillContainer v-for="skillInfo, skillName in skillCollection.skills" :skill="skillName" :level="skillInfo.level" :icon="skillInfo.icon" :isScreenSmall="isScreenSmall"/>
            </div>
        </div>

    </div>
</template>

<style scoped>
    .skills-container
    {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        gap:120px;
    }


    .skills-list
    {
        display: flex;
        justify-content: center;
        gap: 32px;
        flex-wrap: wrap;
    }


    .skills-list-smaller
    {
        gap:8px;
    }

    .skills-collection
    {
        width: 100%;
        max-width: 1100px;

        border-top: 1px solid white;

        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        gap:8px;
    }

    .skills-collection:first-child
    {
        border-top: 0px none white;
    }
    .skills-collection h2
    {
        text-align: center;
        display: flex;
        align-items: center;

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