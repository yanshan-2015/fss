<template>
    <div class="CImg">
        <div class="imgArea">
            <slot></slot>
            <div class="img1">
                <img src="../assets/6-camera.png">
            </div>
        </div>
    </div>
</template>
<style lang="less" scoped>
    .imgArea{
        height: auto;
        padding: 0.15rem 0.27rem 0.27rem 0.1rem;
        background: #fafafa;
        overflow: hidden;
        div{
            position: relative;
            float: left;
            width: 0.8rem;
            height: 0.8rem;
            margin-left: 0.17rem;
            margin-top: 0.27rem;
            background: rgba(20,20,20,0.1);
            border-radius: 8px;
            img{
                width: 100%;
                height: auto;
            }
            span{
                position: absolute;
                right: -0.3rem;
                top: -0.3rem;
                display: inline-block;
                width: 0.213rem;
                height: 0.213rem;
                padding: 0.20rem;
                border-radius: 50%;
                background: url("../assets/6-delete.png")no-repeat center;
            }
        }
    }
</style>
<script>
    export default{
        name: 'CImg'
    }
</script>
