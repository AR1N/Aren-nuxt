<template>
    <div class="container">
        <div class="cover">
            <img id="poster" src="/img/cover_bg.jpg" alt="bg" />
        </div>
        <!-- <div>
            <h1 class="title">nuxt {{ message }}</h1>
        </div> -->
    </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, onUnmounted, ref } from '@vue/composition-api'
// import Parallax from 'parallax'

export default defineComponent({
    setup() {
        const message = ref('This is a message')
        let flag = false
        let timer = null

        onMounted(()=>{
            setImg()
            window.addEventListener('resize',()=>{
                if(!flag){
                    flag = true
                    timer = setTimeout(() => {
                        setImg()
                         flag = false
                    }, 300);
                }
            })
        })
        onUnmounted(()=>{
            window.removeEventListener('resize',()=>{})
        })
       function setImg(){
           let boxH = document.documentElement.clientHeight
		   let boxW = document.documentElement.clientWidth
           let ratio = 1080 / 1920
			const compute = boxH / boxW > ratio;
			let width = compute ? (boxH / ratio + 'px') : `${boxW}px`
            let height = compute ? `${boxH}px` : (boxW * ratio + 'px')
            let poster:HTMLElement = document.getElementById('poster') as HTMLElement
            poster.style.width = width
            poster.style.height = height
            console.log(width,height)
       }
        return {
            message,
        }
    },
})
</script>

<style lang="scss" scoped>
.container {
    .cover {
        height: 100vh;
        width: 100vw;
        overflow: hidden;
        position: relative;
        display: flex;
        align-items: center;
        justify-content: center;
        #poster {
            width: auto;
            position: absolute;
            left: 0;
            right: 0;
            top: 0;
            bottom: 0;
            margin: auto;
            object-fit: cover;
        }
    }
}
</style>
