<template>
    <div id="app">
        <!-- 视图 -->
        <transition name="el-fade-in-linear" mode="out-in">
            <router-view></router-view>
        </transition>
        <!-- 进度条 -->
        <vue-progress-bar></vue-progress-bar>
        <!-- backTop组件 -->
        <my-backTop></my-backTop>
    </div>
</template>
<script>
export default {
    name: 'app',
    methods: {
        init_Progress() {
            this.$router.beforeEach((to, from, next) => {
                this.$Progress.start()
                next()
            })
            this.$router.afterEach(() => {
                this.$Progress.finish()
            })
        }
    },
    created() {
        this.$Progress.start()
        this.init_Progress()
    },
    mounted() {
        this.$Progress.finish()
    }
}
</script>
<style lang='stylus'>
#app {
    position: relative;
    height: 100%;
    min-height: inherit;
}
</style>
