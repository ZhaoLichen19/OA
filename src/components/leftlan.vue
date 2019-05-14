<template>
  <div>
    <el-row class="tac">
      <el-col :span="4">
        <!-- 标题 -->
        <div class="title" @click="back">
          <img src="img/logo.ico" alt>
          <span>学子商城后台</span>
        </div>
        <!-- 登陆用户 -->
        <div class="user">
          <img src="img/user.png" alt>
          <div>
            <span class="sm-hui">欢迎回来</span>
            <br>
            <span>超级管理员</span>
          </div>
        </div>
        <!-- 后台首页 -->
        <div class="back_index">
          <p @click="back">后台首页</p>
        </div>
        <!-- 功能分栏 -->
        <el-menu
          default-active="2"
          class="el-menu-vertical-demo"
          @open="handleOpen"
          @close="handleClose"
          background-color="#545c64"
          text-color="#fff"
          active-text-color="#ffd04b"
        >
          <div class="data-m">
            <span>数据管理</span>
          </div>
          <!-- 商品管理 -->
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>商品管理</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1" @click="list">商品列表</el-menu-item>
              <el-menu-item index="1-2">多条件搜索</el-menu-item>
              <el-menu-item index="1-3">添加商品</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <!-- 用户管理 -->
          <el-submenu index="2">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>用户管理</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1" @click="userList">用户列表</el-menu-item>
              <el-menu-item index="1-2">用户检索</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <!-- 订单管理 -->
          <el-submenu index="3">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>订单管理</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">订单列表</el-menu-item>
              <el-menu-item index="1-2">搜索订单</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <div class="data-m">
            <span>内容管理</span>
          </div>
          <!-- 商品管理 -->
          <el-submenu index="4">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>首页商品管理</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">轮播广告</el-menu-item>
              <el-menu-item index="1-2">首页推荐</el-menu-item>
              <el-menu-item index="1-3">最新上架</el-menu-item>
              <el-menu-item index="1-4">热销单品</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <!-- 用户管理 -->
          <el-submenu index="5">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>功能页面</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">403错误页面</el-menu-item>
              <el-menu-item index="1-2">404错误页面</el-menu-item>
              <el-menu-item index="1-3">500错误页面</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
        </el-menu>
      </el-col>
    </el-row>
  </div>
</template>
<script>
export default {
  data() {
    return {};
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },
    list(){
      this.$router.push("/list")
    },
    back(){
      this.$router.push("/index")
    },
    userList(){
      this.$router.push("/userlist")
    }
  }
};
</script>
<style scoped>
/* 标题 */
.title {
  font-size: 24px;
  color: #fff;
  padding: 1rem;
}
/* 标题图片 */
.title img {
  vertical-align: middle;
}
/* 登陆用户 */
.user {
  color: #fff;
  display: flex;
}
.user img {
  border-radius: 50%;
  width: 3rem;
  height: 3rem;
  border: 3px solid #fff;
  vertical-align: middle;
  margin: 1rem;
}
.user div {
  padding: 1.3rem 0;
}
.user .sm-hui {
  color: #ddd;
  font-size: 14px;
}
/* 返回首页 */
.back_index {
  cursor: pointer;
  color: #fff;
  padding-left: 20px;
}
/* 左侧功能栏 */
.el-col {
  height: 48rem;
  background: #545c64;
}
.el-col-4 {
  width: 215px;
}
/* 数据管理 */
.data-m {
  margin-top: 1rem;
  font-size: 12px;
  color: #fff;
  padding-left: 20px;
}
</style>

