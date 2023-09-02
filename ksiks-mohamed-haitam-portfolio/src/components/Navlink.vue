<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <RouterLink v-if="!isFile" class="router-link-container" :to="href" @mouseenter="isHover = true;" @mouseleave="isHover = false;"> 
        <div class="router-link" >
            <slot></slot> 
            {{ isTextVisible? text: '' }}
        </div>

        <div class="router-link-line" :class="{ 'router-link-line-full': isHover }"></div>
    </RouterLink>

    <a v-else download class="router-link-container" :href="href" @mouseenter="isHover = true;" @mouseleave="isHover = false;"> 
        <div class="router-link" >
            <slot></slot> 
            {{ isTextVisible ? text : '' }}
        </div>

        <div class="router-link-line" :class="{ 'router-link-line-full': isHover }"></div>
    </a>
</template>

<style scoped>
    .router-link-container
    {
        text-decoration: none;
        color: white;
        flex: 1;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        gap: 4px;

    }

    .router-link-container:hover
    {
        color: #FF7700;
    }

    .router-link
    {

        text-align: center;
    }

    .router-link-line
    {
        width: 0%;
        height: 6px;
        background-color: white;
        border-radius: 8px;
        margin-left: 10%;

        align-self: flex-start;
        
        transition: width 0.23s ease-out;
    }

    .router-link-line-full
    {
        width: 80%;
        background-color: #FF7700;
    }
</style>

<script>
    export default
    {
        props:
        {
            href: String,
            text: String,
            isTextVisible: Boolean,
            isFile:
            {
                Type: Boolean,
                default: false
            }
        },
        data() 
        {
            return {
                isHover: false,
            }
        },
    }
</script>