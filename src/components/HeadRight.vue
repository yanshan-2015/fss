<template>
    <div class="HR">
        <slot></slot>
    </div>
</template>
<style lang="less" scoped>
    .HR{
        position: absolute;
        right: 0;
        top: 0;
        z-index: 10;
        width: 1.3rem;
        height: 1.333rem;
        line-height: 1.333rem;
        text-align: center;
        img{
            width: 0.5rem;
            height: auto;
            padding: 0.4rem 0.35rem;
        }
    }
</style>
<script>
    export default{
        name: 'HR',
    }
</script>
