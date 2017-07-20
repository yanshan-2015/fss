<template>
    <div class="CTitle">
        <slot></slot>
    </div>
</template>
<style lang="less" scoped>
    .CTitle{
        padding: 0.4rem 0 0;
        text-align: center;
        h1{
            font-weight: bold;
            font-size: 0.4rem;
            color: #666;
        }
        p{
            font-weight: bold;
            font-size: 0.4rem;
            color: #666;
        }
    }
</style>
<script>
    export default{
        name: 'CTitle',
    }
</script>
