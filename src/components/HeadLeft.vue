<template>
    <div class="HL">
        <slot></slot>
    </div>
</template>
<style lang="less" scoped>
    .HL{
        position: absolute;
        left: 0;
        top: 0;
        z-index: 10;
        width: 1.2rem;
        height: 1.333rem;
        img{
            width: 0.5rem;
            height: auto;
            padding: 0.4rem 0.35rem;
        }
    }
</style>
<script>
     export default{
        name: 'HL',
    }
</script>
