<template>
  <div>
    <div class="celan">
      <my-leftlan></my-leftlan>
    </div>
    <my-header></my-header>
    <div class="container">
      <div class="shuju">
        <div>
          <i class="el-icon-goods"></i>
          <span>上架商品总数</span>
          <span v-text="goodsCount"></span>
        </div>
        <div>
          <i class="el-icon-goods"></i>
          <span>注册用户总数</span>
          <span v-text="userCount"></span>
        </div>
        <div>
          <i class="el-icon-goods"></i>
          <span>已完成订单总数</span>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import myLeftlan from "@/components/leftlan.vue";
import myHeader from "@/components/header.vue";
export default {
  props: ["lid"],
  data() {
    return {
      userCount: 0,
      goodsCount: 0
    };
  },
  created() {
    this.getGoods();
    this.getUser();
  },
  methods: {
    getGoods() {
      //创建变量保存请求地址
      var url = "http://127.0.0.1:3000/getGoods";
      //发送ajax请求，无参数
      this.axios.get(url).then(result => {
        this.goodsCount = result.data[0].c;
      });
    },
    getUser() {
      //创建变量保存请求地址
      var url = "http://127.0.0.1:3000/getUser";
      //发送ajax请求，无参数
      this.axios.get(url).then(result => {
        this.userCount = result.data[0].c;
      });
    }
  },
  components: {
    myLeftlan,
    myHeader
  }
};
</script>
<style scoped>
.celan {
  position: fixed;
  left: 0;
  top: 0;
  z-index: 99;
}
.container {
  margin-left: 215px;
  height: 44.5rem;
  display: flex;
}
.shuju {
  display: flex;
  width: 100%;
}
.shuju div {
  width: 33.3%;
}
canvas {
  background: #d76e8a;
}
</style>
