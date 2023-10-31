<script setup>

</script>


<template>
    <a class="project-card" @mouseenter="hovering = true;" @mouseleave="hovering = false;" :href="link">
        <img :src="getImgUrl" class="project-img" v-if="!isScreenSmall"/>

        <div class="project-data" 
        :class="{'project-data-smaller': isScreenSmall}"
        :style="{'background-image': isScreenSmall? 'url(' + getImgUrl + ')': 'none'}">
            <div class="background-dim" :class="{'background-dim-hover': hovering}" v-if="isScreenSmall"></div>
        
            <h3> 
                {{ title }} 
                <i class="bi bi-link-45deg" v-if="link!=''"></i>
            </h3> 
            
            <div class="project-tools">
                <span class="project-tool" v-for="tool in tools"> {{ tool }} </span>
            </div>

            <div class="project-description" :class="{'project-description-small': isScreenSmall}">
                {{ description }}
            </div>
        </div>
    </a>    
</template>

<style scoped>
    .project-card
    {
        position: relative;
        min-height: 250px;
        width: 100%;

        border-radius: 8px;
        overflow: hidden;

        display: flex;
        justify-content: start;

        color:white;
        text-decoration: none;

        padding: 0px;
        gap: 12px;

        background-color: #2A2550;
        box-shadow: 0px 4px 16px 4px rgba(0, 0, 0, 0.192);

        cursor: pointer;
        transition: transform 0.3s ease-out;

    }

    .project-card:hover
    {
        transform: scale(1.02);
    }


    .project-data
    {
        
        padding: 16px;

        display: flex;
        flex-direction: column;
        justify-content: center;
        gap: 8px;

    }

    .project-data-smaller
    {
        background-size: cover;
        
    }

    .background-dim
    {
        position: absolute;
        left: 0px;
        right: 0px;
        top: 0px;
        bottom: 0px;
        backdrop-filter:brightness(50%) blur(32px);
    }

    .background-dim-hover
    {
        backdrop-filter:brightness(50%);
    }

    .project-data h3
    {
        margin: 0px;
        z-index: 5;

        display: flex;
        align-items: center;
    }

    .project-img
    {
        width: 315px;
        min-width: 315px;
        height: 250px;

        object-fit: cover;
        z-index: 5;

        transition: all 0.2s;
        
    }
    
    .project-tools
    {
        display: flex;
        gap: 5px;
        z-index: 5;
    }

    .project-tool
    {
        border-radius: 16px;
        padding: 4px;
        padding-left: 8px;
        padding-right: 8px;
        font-size: 16px;
        font-weight: bold;
        background-color: #E04D01;
        z-index: 5;
    }

    .project-description
    {
        flex: 1;
        display: flex;
        align-items: center;
        font-size: x-large;
        z-index: 5;
    }

    .project-description-small
    {
        font-size: x-large;
    }

</style>

<script>


    export default
    {
        props:
        {
            id: {
                type:String,
                default: "",
            },
            title: String,
            images: Array,
            main: Number,
            tools: Array,
            description: String,
            link: String,
            isScreenSmall: Boolean
        },
        data()
        {
            return {
                hovering: false,
                currentImage: 0,
                switchImageIntervalId: -1,
            };
        },
        mounted()
        {

            /*this.switchImageIntervalId = setInterval(() => {
                if (this.images.length == 0) return;
                // skip main
                do
                {
                    this.currentImage = (this.currentImage + 1) % this.images.length;
                } while (this.currentImage == this.main);
            }, 2000);*/
        },
        unmounted()
        {
            /*clearInterval(this.switchImageIntervalId);*/
        },
        computed:
        {
            getImgUrl() 
            {
                return new URL(`../assets/projects/images/${this.id}/${this.images[this.hovering? this.currentImage: this.main]}`, import.meta.url).href;   
            }
        }
    }
</script>