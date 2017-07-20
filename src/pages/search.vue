<template>
  <div class="search" v-bind:style="{'min-height': height+'px'}">
    <div class="header">
        <head-left>
            <img src="../assets/2-back.png" @click="back">
        </head-left>
        <head-name>
            <p>经销商星级评分</p>
        </head-name>
        <head-right>
            <img src="../assets/2-history.png" @click="history">
        </head-right>
    </div>

    <div class="picBox">
      <img src="../assets/2-pic.png" alt="">
    </div>

    <div class="searchBox">
      <input v-model="keyWord" type="text" placeholder="请输入关键字（经销商名或地区）">
      <span v-on:click="clearKey"></span>
    </div>

    <div class="resultBox">
      <h3>店铺名</h3>
      <p v-show='unMsg'>搜索不到相关内容！</p>
      <ul>
        <li class="clearfix" @click="toRatingStart(index,resultList)" v-for="(result,index) in resultList">
          <p>{{result.name}}</p>
          <div>
            <span v-bind:style="{background: 'url(../static/images/star'+result.last_result+'.png) no-repeat'}"></span>
            <p>上次评星 {{result.last_result_date}}</p>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
// import headerComponent from '../components/header-component'
    import HeadLeft from '@/components/HeadLeft.vue'
    import HeadName from '@/components/HeadName.vue'
    import HeadRight from '@/components/HeadRight.vue'
    import {path} from '../common/variable.js'
  export default{
    name: 'search',
    components: { HeadLeft, HeadName, HeadRight },
    data () {
      return {
        height: window.innerHeight,
        userNum: this.$route.params.num,
        keyWord: '',
        resultList: [],
        starSum: [5,5,0,0],
        unMsg: false,
        canGetData: true
      }
    },
    watch:{
      'keyWord':function(val){
        if(val == ''){
          this.resultList = [];
          this.unMsg = false;
        }else{
          if(this.canGetData){
            this.canGetData = false;
            this.$http.jsonp(path+'crm2/getStoreInfo.do', {
              jsonp: 'jsoncallback',
              params: {
                keyWord: val,
                pageSize: 50,
                currentPage: 1,
                searchType: ''
              }
            })
            .then(function(data) {
              if(data.status == 200){
                this.canGetData = true;
                data = eval('(' + data.bodyText + ')');
                this.resultList = data[0].storeList;
                //返回数组长度为0时，显示没数据提示文本。
                if(data[0].storeList.length == 0){
                  this.unMsg = true;
                }else{
                  this.unMsg = false;
                }
              }else{
                alert('网络故障，请求失败！')
              }
            })
          }
        }
      }
    },
    methods:{
      toRatingStart:function(index,resultList){
        this.$router.push({ path: '/startRating/'+this.resultList[index].name+'/'+resultList[index].reverse1+'/'+resultList[index].id+'/'+this.userNum});
      },
      clearKey:function(){
        this.keyWord = '';
      },
        back() {
            this.$router.back();
        },
        history() {
            this.$router.push({ path: '/history '});
        }
    }
  }
</script>

<style lang="less" scoped>
@import "../less/variable.less";
.header{
    position: relative;
}
.search{
  background: @bgc;
}
.picBox{
  height: 2.66667rem;
  background: @fc;
  img{
    height: 1.3333rem;
    margin-top: .666667rem;
  }
}
.searchBox{
  height: 2.13333rem;
  background: @fc;
  position: relative;
  input{
    display: block;
    width: 92%;
    height: 1.06667rem;
    margin: 0 auto;
    border-radius: 1.06667rem;
    background: @bgc;
    padding-left: .5333rem;
    box-sizing: border-box;
  }
  span{
    display: block;
    width: .346667rem;
    height: .346667rem;
    background: url(../assets/8-clos.png) no-repeat;
    background-size: 100% 100%;
    position: absolute;
    top: .36rem;
    right: .93333rem;
  }
}
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

