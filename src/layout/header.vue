<template>
    <header id="header" class="">
        <div class="header_wrap">
            <router-link class="logo" to="/">订阅号</router-link>
            <div class="right">
                <!-- <router-link :to="{name: 'publish'}">
                    <el-button type="primary" class="publish_btn">发表</el-button>
                </router-link> -->
                <el-dropdown class="user" @command="handleCommand" placement='bottom'>
                    <div class="userinfo">
                        <img :src="user.icon" alt="">
                        <span class="el-dropdown-link">{{user.name}}</span>
                    </div>
                    <el-dropdown-menu slot="dropdown">
                        <el-dropdown-item command="exit">退出</el-dropdown-item>
                    </el-dropdown-menu>
                </el-dropdown>
            </div>
        </div>
    </header>
</template>
<script>
import { mapState, mapMutations } from 'vuex'
export default {
    computed: {
        ...mapState([
            'user'
        ])
    },
    methods: {
        ...mapMutations([
            'set_user',
            'remove_token'
        ]),
        handleCommand(command) {
            if (command === 'exit') {
                this.remove_token()
                this.$router.push('/login')
            }
        }
    }
}
</script>
<style lang='stylus'>
#header {
    position: relative;
    box-shadow: 0 1px 4px 0 rgba(0, 0, 0, .12);
    border-top: 4px solid appColor;
    height: 76px;
    background: #fff;
    min-width: 1138px;
    .header_wrap {
        position: relative;
        margin: 0 auto;
        width: 1138px;
        height: 100%;
        z-index: 100;
        .logo {
            position: absolute;
            color: transparent;
            top: 50%;
            left: 0;
            width: 94px;
            height: 32px;
            background: url(../assets/img/logo.png)no-repeat;
            background-size: contain;
            transform: translateY(-50%);
        }
        .right {
            height: 100%;
            float: right;
            display: flex;
            align-items: center;
            .publish_btn {}
            .user {
                margin-left: 40px;
                .userinfo {
                    img {
                        width: 40px;
                        height: 40px;
                        border-radius: 100%;
                        vertical-align: middle;
                        margin-right: 5px;
                    }
                }
            }
        }
    }
}
</style>