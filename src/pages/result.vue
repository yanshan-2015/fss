<template>
  <div class="result" v-bind:style="{'min-height': height+'px'}">
    <div class="header">
      <head-left>
          <img src="../assets/2-back.png" @click="back">
      </head-left>
      <head-name>
        <p>查询结果</p>
      </head-name>
    </div>

    <div class="resultBox">
      <h3>店铺名</h3>
      <ul>
        <li class="clearfix" @click="toRatingStart(index,storeResults)" v-for="(storeResult,index) in storeResults">
          <p>{{storeResult}}</p>
          <div>
            <span v-bind:style="{background: 'url(../static/images/star'+starSum[index]+'.png) no-repeat'}"></span>
            <p>上次评星 2017.01.01</p>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>
<style lang="less" scoped>
@import "../less/variable.less";

.resultBox{
  text-align: left;
  padding: 0 .4rem;
  h3{
    font-size: @f26;
    line-height: 2em;
    padding-top: .106667rem;
    border-bottom: 1px solid #e5e5e5;
    color: #999;
  }
  ul{
    li{
      border-bottom: 1px solid #e5e5e5;
      padding: .2rem 0;
      &>p{
        width: 65%;
        font-size: @f32;
        line-height: 1.2em;
        color: #666;
        float: left;
      }
      div{
        width: 35%;
        text-align: right;
        float: left;
        span{
          display: block;
          width: 100%;
          height: .346667rem;
          background-size: auto .346667rem!important;
          background-position: right 0 top 0!important;
        }
        p{
          font-size: @f22;
          color: #ff7559;
        }
      }
    }
  }
}
</style>
<script>
// import headerComponent from '../components/header-component'
    import HeadLeft from '@/components/HeadLeft.vue'
    import HeadName from '@/components/HeadName.vue'
  export default{
    name: 'search',
    components: { HeadLeft, HeadName },
    data () {
      return {
        height: window.innerHeight,
        storeResults: ['东莞市厚街镇3D专卖店东莞市厚街镇3D专卖店东莞市厚街镇3D专卖店','东莞市厚街镇3D专卖店','东莞市厚街镇3D专卖店','东莞市厚街镇3D专卖店'],
        starSum: [5,5,0,0]
      }
    },
    methods:{
      back() {
        this.$router.go(-1);
      },
      toRatingStart:function(index,storeResults){
        this.$router.push({ path: '/startRating/'+this.storeResults[index]});
      }
    }
  }
</script>
