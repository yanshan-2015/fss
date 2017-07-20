<template>
    <div class="dialog cover">
        <div class="contain">
            <slot></slot>
        </div>
    </div>
</template>
<style lang="less" scoped>
    .cover{
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 100;
        background: rgba(24,24,24,0.8);
        .contain{
            position: absolute;
            top: 0;
            right: 0;
            bottom: 0;
            left: 0;
            margin: auto;
        }
    }
</style>
<script>
    export default{

    }
</script>
