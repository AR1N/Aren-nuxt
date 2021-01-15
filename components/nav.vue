<template>
    <div class="nav">
        <div class="wrapper">
            <div class="item">1</div>
            <div class="item">2</div>
            <div class="item">3</div>
        </div>
    </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.nav{
  height: 66px;
  width:100vw;
  position: fixed;
  top: 0;
  color: #fff;
  z-index: 999;
  background:rgba(255, 255,255,.5);
  .wrapper{
      height: 100%;
      margin: 0 auto;
      max-width: 780px;
      display: flex;
      align-items: center;
      justify-content: space-around;
      .item{
          font-weight: bold;
          background-color: cornflowerblue;
      }
  }
}
</style>>

