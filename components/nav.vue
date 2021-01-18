<template>
    <div class="nav">
        <div class="wrapper">
            <div class="item" v-for="(item,index) in navData" :key='index'>
                <nuxt-link  class="item" :to="item.path">{{item.title}}</nuxt-link>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, onUnmounted, ref } from '@vue/composition-api'

export default defineComponent({
    props:{
        navData:{
            type:Array,
            require:true,
            default:()=>{
                return [
                    {title:'导航一',path:'/'},
                    {title:'导航二',path:'/second'}
                ]
            }
        }
    },
    setup(props,context){
        console.log(props,context)
    }
})
</script>

<style lang="scss" scoped>
.nav{
  height: 66px;
  width:100vw;
  position: fixed;
  top: 0;
  color: #fff;
  z-index: 999;
  background:rgba(0, 0,0,.2);
  .wrapper{
      height: 100%;
      margin: 0 auto;
      max-width: 780px;
      display: flex;
      align-items: center;
      justify-content: space-around;
      .item{
          height: 100%;
          width: 100%;
          display: flex;
          align-items: center;
          justify-content: center;
          font-size: 18px;
          font-weight: bold;
          cursor: pointer;
          &:hover{
              background-color: cornflowerblue;
          }
      }
  }
}
</style>>

