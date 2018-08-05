<template>
  <div class="star">
    <span class="star-item" v-bind:class="itemClass" v-for="(itemClass,index) in itemClasses" :key="index"></span>
  </div>
</template>

<script>
  /*星星的长度*/
  const LENGTH= 5
  /*星星的状态*/
  const  Cls_on = 'on'

  const  Cls_half = 'half'

  const  Cls_off = 'off'


  export default {
    name: '',
    props:{
        score:{
        type: Number
      }
    },
    data () {
      return {

      }
    },
    computed:{
      itemClasses(){
        let result=[]

        //分数计算
        let score = Math.floor(this.score*2)/2

        //半星   对分数进行取余
        let hasDecimal = score%1!=0

        //全星
        let integer = Math.floor(score)

        //遍历全星
        for(let i=0;i<integer;i++){
            result.push(Cls_on)
        }

        if(hasDecimal){
            result.push(Cls_half)
        }

        //补齐
        while(result.length<LENGTH){
            result.push(Cls_off)
        }
        console.log(result);
        return result;
        console.log(result);

      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .star{
    font-size: 0;
  }
  .star .star-item{
    display: inline-block;
    width: 10px;
    height: 10px;
    margin-right: 3px;
    background-repeat: no-repeat;
    background-size: 10px 10px;
  }
  .star .star-item:last-child{
    margin-right: 0;
  }

  /* 三种图片类型*/
  .star .on{
    background-image: url(img/star24_on@2x.png);
  }
  .star .half{
    background-image: url(img/star24_half@2x.png);
  }
  .star .off{
    background-image: url(img/star24_off@2x.png);
  }
</style>
