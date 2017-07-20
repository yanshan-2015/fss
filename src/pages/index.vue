<template>
    <div class="index">
        <p>index</p>
        <router-link to="/search">搜索</router-link>
        <router-link to="/history">我的记录</router-link>
        <router-link to="/result">查询结果</router-link>
    </div>
</template>
<style lang="less" scoped>
@import "../less/variable.less";
p{
    width: 10rem;
}
</style>
<script>
    export default{

    }
</script>
