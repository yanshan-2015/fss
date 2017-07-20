<template>
    <div class="HN">
        <slot></slot>
    </div>
</template>
<style lang="less" scoped>
    @import "../less/variable";
    .HN{
        width: 100%;
        height: 1.33rem;
        text-align: center;
        line-height: 1.33rem;
        p{
            font-size: 0.51rem;
            color: @subfc;
        }
    }
</style>
<script>
     export default{
        name: 'HN',
    }
</script>
