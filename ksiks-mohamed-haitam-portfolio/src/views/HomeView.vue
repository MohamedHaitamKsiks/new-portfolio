<script setup>
import '../assets/main.css';
</script>

<template>

    <div class="home-container" :class="{ 'home-container-vertical': isScreenSmall }">
        <div class="home-title-container">
            <h1 class="home-title" :class="{ 'home-title-smaller': isScreenSmall }">
                Hi There! <br/>
                I'm <strong class="highlight"> Ksiks Mohamed Haitam </strong>
            </h1>

            <h2 class="home-subtitle" :class="{'home-subtitle-smaller': isScreenSmall}">
                /** {{ currentText }} <span :class="{'cursor-invisible': isCursorVisible}"> | </span> **/
            </h2>
        </div>

        <img draggable="false" v-if="isAvatar" src="~@/assets/images/avatar.jpg" @click="isAvatar = false;"/>
        <img draggable="false" v-if="!isAvatar" src="~@/assets/images/profile.jpg" @click="isAvatar = true;"/>
    </div>
</template>

<style scoped>
    .cursor-invisible
    {
        opacity: 0%;
    }

    .home-container
    {
        height: 100vh;

        display: flex;
        justify-content: space-around;
        align-items: center;
    }

    .home-container-vertical
    {
        flex-direction: column-reverse;
    }

    .home-title
    {
        font-weight: normal;
        margin: auto;
    }

    .home-title-smaller
    {
        font-size: 40px;
    }

    .home-subtitle
    {
        font-weight: lighter;
        color: rgba(255, 255, 255, 0.586);
    }

    .home-subtitle-smaller
    {
        font-size: 24px;
    }

    .home-container img
    {
        border-radius: 100%;
        width: 70%;
        max-width: 500px;
        user-select: none;
        cursor: pointer;

        transition: transform 0.2s ease-out;
    }

    .home-container img:hover
    {
        transform: scale(1.05);
    }

</style>

<script>

    export default
    {
        mounted() {
            // lister to windows resize
            window.addEventListener('resize', this.onWindowResize);
            this.onWindowResize();

            // animate cursor
            this.cursorAnimationIntervalId = setInterval(() => {
                this.isCursorVisible = !this.isCursorVisible;
            }, 400);
            
            //animate text to write and delete
            this.animationStepIntervalId = setInterval(() => {
                // write text
                if (this.currentAnimationState == "write")
                {
                    // get 
                    let jobName = this.jobList[this.currentJobIndex];

                    do
                    {
                        // write text
                        this.currentText += jobName[this.cursor];

                        // move cursor
                        this.cursor += 1;
                        if (this.cursor == jobName.length) {
                            this.currentAnimationState = "pause";
                            return;
                        }

                    } while( jobName[this.cursor] == " ")


                }
                // wait for timer to reach pause duration
                else if (this.currentAnimationState == "pause")
                {
                    if (this.pauseTimer < this.pauseDuration) 
                    {
                        this.pauseTimer++;
                    }
                    else 
                    {
                        this.currentAnimationState = "erase";
                        this.pauseTimer = 0;
                    }
                }
                // erase written text then call write for new one
                else
                {
                    if (this.currentText.length > 0)
                    {
                        do 
                        {
                            this.currentText = this.currentText.slice(0, this.currentText.length - 1);
                        } while (this.currentText[this.currentText.length - 1] == " ");
                    }
                    else
                    {
                        // set new job to write
                        this.currentJobIndex = (this.currentJobIndex + 1) % this.jobList.length;
                        this.cursor = 0;
                        this.currentAnimationState = "write";
                    }
                }

            }, this.animationTickDuration);
            
        },
        unmounted() {
            window.removeEventListener('resize', this.onWindowResize);
            clearInterval(this.cursorAnimationIntervalId);
            clearInterval(this.animationStepIntervalId);
        },
        data() {
            return {
                isAvatar: true,

                isScreenSmall: false,

                isCursorVisible: false,

                currentJobIndex: 0,
                jobList: ["Software Engineer", "Game Developer"],
                currentText: "",
                
                // write | pause | erase
                animationTickDuration: 50, // in ms,
                currentAnimationState: "write",
                pauseDuration: 20, // in animation ticks
                pauseTimer: 0,
                cursor: 0,

                cursorAnimationIntervalId: -1,
                animationStepIntervalId: -1
            };
        },
        methods:
        {
            onWindowResize() {
                const thresholdWidth = 950;
                this.isScreenSmall = window.innerWidth < thresholdWidth;
            }
        }
    }
    
</script>
