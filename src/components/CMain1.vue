<template>
    <div class="CMain1">
        <slot></slot>
    </div>
</template>
<style lang="less" scoped>
    .CMain1{
        width: 92%;
        margin: 0 auto;
        padding: 0.35rem 0;
        text-align: left;
        p{
            line-height: 0.5rem;
            font-size: 0.35rem;
            color: #666;
            text-indent: 2em;
        }
    }
</style>
<script>
    export default{
        name: 'CMain1'
    }
</script>
