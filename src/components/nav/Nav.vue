<template>
  <div class="nav">
    <router-link class="nav-item" to="/goods">
      点菜
      <i class="line"></i>
    </router-link>
    <router-link class="nav-item" to="/ratings">
      评价({{commentNum}})
      <i class="line"></i>
    </router-link>
    <router-link class="nav-item" to="/seller">
      商家
      <i class="line"></i>
    </router-link>
  </div>
</template>

<script>
  export default {
    name: '',
    data () {
      return {

      }
    },
    props:{
      commentNum:{
        type:Number,
        default:"0"
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .nav{
    display: flex;
    width: 100%;
    height: 40px;
    line-height:40px;
    border-bottom: 1px solid #e4e4e4;
    .nav-item{
      flex: 1;
      text-align: center;
      font-size: 13px;
      text-decoration: none;
      color: #666;
      position: relative;
    }
    .active{
      color: #ffbb22;
      .line{
        width: 20px;
        height: 2px;
        display: block;
        position: absolute;
        left: 50%;
        margin-left: -10px;
        bottom: -1px;
        background: #ffbb22;
      }
    }
  }
</style>
