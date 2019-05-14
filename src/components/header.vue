<template>
  <div>
    <header>
      <ul class="user">
        <a>
          <img src="img/user.png">
          <span v-text="uname"></span>
          <span v-text="zx_dl" @click="logout"></span>
        </a>
      </ul>
    </header>
  </div>
</template>
<script>
export default {
  data() {
    return {
      uname: "",
      zx_dl:"请登陆"
    };
  },
  created() {
    //创建变量保存请求地址
    var url = "http://127.0.0.1:3000/getUname";
    //发送ajax请求，无参数
    this.axios.get(url).then(result => {
      console.log(result)
      this.uname = result.data.uname;
      this.zx_dl="注销"
    });
  },
  methods:{
     logout(){
       this.$router.push("login")
     }
  }
};
</script>
<style scoped>
/* 头部 */
header {
  height: 3.5rem;
  background: rgba(204, 214, 214, 0.5);
  line-height: 3.5rem;
  position: relative;
}
.user {
  position: absolute;
  right: 2rem;
  margin: 0;
}
.user img {
  width: 40px;
  height: 40px;
  vertical-align: middle;
  border-radius: 50%;
}
</style>
