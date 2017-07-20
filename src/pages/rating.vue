<template>
  <div class="rating" v-bind:style="{'min-height': height+'px'}">
    <div class="header">
      <button class="back" v-on:click="back"></button>
      <h1>评星进行中123</h1>
    </div>

    <form id="imgForm" method="post" enctype="multipart/form-data">  
      <input type="file" id="xdaTanFileImg"  multiple="multiple"  name="head_url"  v-on:change="xmTanUploadImg"/>  

      <div class="img-box" id="imgboxid">  

      </div>  
      
      <div id="xmTanDiv"></div><br/>  
      <div id="errordiv"   style="margin-top:15px;width:100%;text-align:center;">  
      </div>  
    </form>

    <span style="display: block;margin-top: 80px;" v-on:click="upload">上传</span>

    <img class="img" src="" alt="">
    
  </div>
</template>
<style lang="less" scoped>
@import "../less/variable.less";

</style>
<script>
import $ from 'n-zepto'
  export default{
    name: 'rating',
    data () {
      return {
        height: window.innerHeight
      }
    },
    methods:{
      back:function(){
        this.$router.go(-1);
        return false;
      },
      upload:function(){
        var formData = new FormData($( "#imgForm" )[0]);
        // formData.append("msg","123");
        console.log(formData);
        $.ajax({  
          url: 'http://10.11.0.206:8866/CrmApp/crm/updateImage.do' ,  
          type: 'POST',  
          data: formData,  
          async: false,  
          cache: false,  
          contentType: false,  
          processData: false,  
          success: function (returndata) {  
              console.log(returndata);  
          },  
          error: function (returndata) {  
              console.log(returndata);  
          }  
        });
      },
      // imgInput:function(e){
      //   let file = e.target.files[0];
      //   var imgurl = e.target;
      //   console.log(e);
      //   console.log(imgurl);
      // },
      //选择图片，马上预览  
      xmTanUploadImg:function(obj) { 
        obj = obj.target;
        console.log(obj);
        var fl=obj.files.length; 
        console.log(fl);
        for(var i=0;i<fl;i++){  
          var file=obj.files[i];  
          console.log(file);
          var reader = new FileReader();  
          console.log(reader);
          //读取文件过程方法  
          reader.onloadstart = function (e) {  
              console.log("开始读取....");  
          }  
          reader.onprogress = function (e) {  
              console.log("正在读取中....");  
          }  
          reader.onabort = function (e) {  
              console.log("中断读取....");  
          }  
          reader.onerror = function (e) {  
              console.log("读取异常....");  
          }  
          reader.onload = function (e) {  
            console.log("成功读取....");  

            var imgstr='<img style="width:100px;height:100px;" src="'+e.target.result+'"/>';  
            var oimgbox=document.getElementById("imgboxid");  
            var ndiv=document.createElement("div");  

            ndiv.innerHTML=imgstr;  
            ndiv.className="img-div";  
            oimgbox.appendChild(ndiv);                 
          }  
          reader.readAsDataURL(file);   
        }   
      }/*,
      submit:function(){
        $.post("http://10.11.0.206:8866/CrmApp/crm/getVerifyUserInfo.do",{username:'11610129',password:'123456'},function(result){
          console.log(123);
          alert(JSON.stryingify(result));
        });
        var arr = [];
        // console.log(123);
        //   var path = $('.img-box .img-div img').value;
        //   console.log(path);
        $('.img-box .img-div img').each(function(){

          var str = $(this).attr('src');
          arr.push(str);
          console.log(str.length);
          console.log(typeof(str));
        });
        this.imgUrl = arr;
        console.log(this.imgUrl);
      }*/
    },
    mounted:function(){
      // xmTanUploadImg();
    }
  }
</script>
