<template>
    <div class="CHead">
        <slot></slot>
    </div>
</template>
<style lang="less" scoped>
    .CHead{
        position: absolute;
        left: 0;
        bottom: 0;
        z-index: 1;
        width: 82%;
        height: 0.66rem;
        p{
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            margin-left: 0;
            text-align: left;
            font-weight: bold;
            font-size: 0.38rem;
            color: #999;
            i{
                font-style: normal;
                font-weight: bold;
                font-size: 0.38rem;
                color: #ff7559;
            }
        }
    }
</style>
<script>
    export default{
        name: 'CHead'
    }
</script>
