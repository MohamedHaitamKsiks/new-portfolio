<template>
    <div class="skill-container" @mouseenter="hovering = true;" @mouseleave="hovering = false;">
        
        <div class="skill" :class="{'skill-smaller': isScreenSmall, 'skill-container-bigger': !isScreenSmall}">
            <i :class="'skill-icon ' + icon"></i>
            <div class="skill-name" v-if="icon==''"> {{ skill }} </div>
            <div class="skill-level" :style="{'top': hovering?(100 - level) + '%':'100%'}"></div>
        </div>
    </div>
</template>

<style scoped>
    .skill-container
    {
        cursor: pointer;
        
    }

    .skill-container-bigger
    {
        transition: transform 0.3s ease-out;
    }

    .skill-container-bigger:hover
    {
        transform: scale(1.1);
    }

    .skill-name
    {
        z-index: 1;
    }

    .skill
    {
        position: relative;

        display: flex;
        justify-content: center;
        align-items: center;

        width: 240px;
        height: 160px;

        border: 1px solid white;
        border-radius: 8px;

        padding: 10px;
        overflow: hidden;

    }

    .skill-icon
    {
        font-size: 80px;
        z-index: 1;
    }

    .skill-smaller
    {
        width: 140px;
        height: 120px;
        
    }

    .skill-level
    {
        position: absolute;
        left: 0px;
        right: 0px;
        bottom: 0px;
        background-color: #E04D01;

        transition: top 0.2s ease-out;

    }
</style>

<script>
    export default
    {
        props:
        {
            skill: String,
            level: Number,
            icon: String,
            isScreenSmall: Boolean
        },
        data()
        {
            return {
                realLevel: 0,
                timeoutId: -1,
                hovering: false
            }
        },
        mounted()
        {
            this.timeoutId = setTimeout(() => {
                this.realLevel = this.level;
            }, 10);
        },
        unmounted()
        {
            clearTimeout(this.timeoutId);
        }
    }
</script>
