<template>
  <div id="app">
    <!--header头部-->
    <app-header v-bind:Info="poiInfo"></app-header>

    <!--nav导航-->
    <app-nav :commentNum="commentNum"></app-nav>

    <!--路由出口-->
    <keep-alive>
      <router-view></router-view>
    </keep-alive>
  </div>
</template>

<script>
  import Header from './components/header/Header'
  import Nav from './components/nav/Nav'
  export default {
    name: 'App',
    data(){
        return{
            poiInfo:{},
            commentNum:0,
        }
    },
    components:{
        "app-header" : Header,
        "app-nav" : Nav
    },
    created(){
        //axios
        //fetch
      fetch("api/goods").then(res=>{
          return res.json()
      }).then(response=>{
          if(response.code==0){
              this.poiInfo=response.data.poi_info;
              console.log(this.poiInfo);
          }
      })

      //请求ratings
      fetch("api/ratings").then(res=>{
          return res.json()
      }).then(response=>{
          if(response.code==0){
              //this.commentNum=response.data.poi_info;
              this.commentNum=response.data.comment_num;
              //console.log(response.data.comment_num);
          }
      })
    }
  }
</script>

<style>

</style>
