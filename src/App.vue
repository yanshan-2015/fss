<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
import Vue from 'vue'
import vueResource from 'vue-resource'
Vue.use(vueResource)

import {flexible} from './common/properScreen.js'
import {flexibleCss} from './common/properScreen_css.js'
flexible();
flexibleCss();



export default {
  name: 'app'
}
</script>

<style lang="less">
@import "./less/variable.less";
  /*reset css */
body,dl,dd,ul,ol,h1,h2,h3,h4,h5,h6,pre,form,fieldset,legend,input,textarea,p,thead,tbody,tfoot,th,td {margin:0;padding:0}  
ul,ol{list-style-type:none;list-style-image:none}
a{text-decoration:none}a:active{background-color:transparent}  a:active,a:hover{outline:0 none}a:focus{outline:1px dotted}  
html{-ms-text-size-adjust:100%;-webkit-text-size-adjust:100%;text-size-adjust:100%;font-size:62.5%}  
body{font-size:14px;line-height:1.8}
h1,h2,h3,h4,h5,h6{font-weight:400}h1{font-size:36px}h2{font-size:30px}h3{font-size:22px}h4{font-size:18px}h5{font-size:14px}h6{font-size:12px}
a:link,a:visited,a:hover,a:active{text-decoration: none;}
a,button{
    outline:none;
    -webkit-tap-highlight-color: transparent;
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -webkit-tap-highlight-color: rgba(0,0,0,0); 
}
button,input,textarea{
    border: none;
    background: none;
    outline: none;
}
textarea{overflow: hidden;}

h3{
  color: #666;
}
p,li,span,input,label,div{
  color: #999;
}

a:hover{text-decoration:none;}

/* common css */
.hide{
  display: none;
}

.left {
  float: left;
}

.right {
  float: right;
}

.clear {
  clear: both;
}

.clearfix {
  *zoom: 1;
  &:before {
    display: table;
    line-height: 0;
    content: "";
  }
  &:after {
    display: table;
    line-height: 0;
    content: "";
    clear: both;
  }
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #999;
}

/* common css */
.header{
  height: 1.3333rem;
  background: @fc;
  position: relative;
  h1{
    font-size: @f38;
    line-height: 1.3333rem;
    color: @subfc;
    font-weight: bold;
  }
  button{
    display: block;
    width: .48rem;
    height: .48rem;
    position: absolute;
    top: 50%;
    margin-top: -.24rem;
    background: url(./assets/2-back.png) no-repeat;
    background-size: 100% 100%;
    left: .4rem;
  }
  a{
    width: .48rem;
    height: .48rem;
    background: url(./assets/2-history.png) no-repeat;
    background-size: 100% 100%;
    position: absolute;
    top: 50%;
    right: .4rem;
    margin-top: -.24rem;
  }
}
</style>
