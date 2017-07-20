<template>
  <div class="ratingStart">
    <div class="header">
        <head-left>
            <img src="../assets/2-back.png" @click="back">
        </head-left>
        <head-name>
            <p>开始评星</p>
        </head-name>
    </div>
    
    <div class="storeMsgBox">
      <img src="../assets/5-pic.png">
      <h2>{{name}}</h2>
      <span>三-六级城市</span>
    </div>

    <ul class="stars clearfix">
      <li class="starLis" v-for="(star,index) in stars">
        <div class="starList" @click="starSelect(index,stars)" v-bind:style="{'background-image': 'url(static/images/star'+(index+1)+'.png)'}"></div>
        <p>{{star}}</p>
      </li>
      <li class="startLi"><button class="startBtn" v-on:click="startRating">开始评星</button></li>
    </ul>
    
  </div> 
</template>

<script>
import {path} from '../common/variable.js'
import Vue from 'vue'
import vueResource from 'vue-resource'
import HeadLeft from '@/components/HeadLeft.vue'
import HeadName from '@/components/HeadName.vue'
  export default{
    name: 'search',
    components: { HeadLeft, HeadName },
    data () {
      return {
        height: window.innerHeight,
        name: this.$route.params.name,
        city: this.$route.params.city,
        id: this.$route.params.id,
        num: this.$route.params.num,
        stars: ['一星','二星','三星','四星','五星'],
        star: 0,
        flownum: ''
      }
    },
    methods:{
      back() {
        this.$router.back();
      },
      starSelect:function(index,stars){
        this.star = 'S'+(index+1);
      },
      startRating:function(){
        if(this.star != 0){
          this.$router.push({ path: '/check/'+this.city+'/'+this.star+'/'+this.id+'/'+this.name+'/'+this.num+'/'+this.flownum+'/1'})
        }else{
          alert('请选择评星等级');
        }
        return false;
      }
    },
    mounted:function(){
      $('.starLis').click(function(){
        $(this).addClass('on');
        $(this).siblings().removeClass('on');
      })
      //获取流水号
      this.$http.jsonp(path+'crm/getFlowNum.do', {
        jsonp: 'jsoncallback',
        params: {
          store_id: this.id
        }
      })
      .then(function(data) {
        var status = data.body[0].STATUS;
        if(status == 0){
          this.flownum = data.body[0].FLOWNUMBER;
        }else{
          //如果流水号不存在（status=-1）或该流程已完成（status=1），则产生一个流水号
          if(this.flownum == ''){
              this.$http.jsonp(path+'crm/getFlowNumber.do', {
                jsonp: 'jsoncallback'
              })
              .then(function(data) {
                  this.flownum = data.body.flowNumber;
              })
          }
        }
      })
    }
  }
</script>

<style lang="less" scoped>
@import "../less/variable.less";
.storeMsgBox{
  background: @bgc;
  img{
    height: 1.33333rem;
    margin-top: 1.7rem;
  }
  h2{
    font-size: @f38;
    color: @subfc;
    line-height: 1.4em;
    padding: .2rem .4rem;
  }
  span{
    font-size: @f28;
    padding-left: .586667rem;
    background: url(../assets/5-cituy.png) no-repeat;
    background-size: auto .4rem;
  }
}
ul.stars{
  padding: 0 .4rem;
  li{
    width: 32%;
    border: 1px solid #e5e5e5;
    border-radius: .133333rem;
    box-sizing: border-box;
    float: left;
    margin-right: 2%;
    margin-top: .24rem;
    position: relative;
    p{
      font-size: @f26;
      line-height: .8rem;
      border-top: 1px solid #e5e5e5;
      margin-top: 1.06667rem;
    }
    p:hover{
      color: @subfc;
    }
    div{
      width: 100%;
      height: 1.06667rem;
      padding-bottom: .8rem;
      position: absolute;
      top: 0;
      left: 0;
      background-repeat: no-repeat;
    }
  }
  li.on:nth-child(1) div{
    background-image: url(../assets/unstar1.png)!important;
  }
  li.on:nth-child(2) div{
    background-image: url(../assets/unstar2.png)!important;
  }
  li.on:nth-child(3) div{
    background-image: url(../assets/unstar3.png)!important;
  }
  li.on:nth-child(4) div{
    background-image: url(../assets/unstar4.png)!important;
  }
  li.on:nth-child(5) div{
    background-image: url(../assets/unstar5.png)!important;
  }
  li:nth-child(1) div,li:nth-child(2) div,li:nth-child(3) div{
    background-size: auto .86667rem!important;
    background-position: center .1rem!important;
  }
  li:nth-child(4) div,li:nth-child(5) div{
    background-size: auto .41117rem!important;
    background-position: center .31111rem!important;
  }
  li:nth-child(3){
    margin-right: 0;
  }
  li.on{
    background: @fc;
    p{
      color: @subfc;
    }
  }
}
li.startLi{
  width: 100%!important;
  box-sizing: border-box;
  border: none!important;
}
li.startLi:hover{
  background: none!important;
}
.startBtn{
  display: block;
  width: 100%;
  margin: .53333rem 0;
  color: @subfc;
  font-size: @f34;
  line-height: 1.066667rem;
  border-radius: .12rem;
  box-sizing: border-box;
  background: @fc;
}
</style>
