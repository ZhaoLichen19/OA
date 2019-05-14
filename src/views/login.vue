<template>
  <div class="app-login">
    <h3>管理员登陆</h3>
    <form action="#">
      <input v-model="name" type="text" placeholder="管理员登录名">
      <br>
      <span v-text="nameMsg"></span>
      <br>
      <input v-model="pwd" type="password" placeholder="管理员登陆密码">
      <br>
      <span v-text="pwdMsg"></span>
      <br>
      <input @click="btnLogin" type="button" value="登陆">
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: "",
      pwd: "",
      nameMsg: "",
      pwdMsg: ""
    };
  },
  methods: {
    btnLogin() {
      //功能;获取用户输入的用户名密码
      //验证如果通过发送ajax请求给服务器程序并且返回结果
      //1、获取用户输入的用户名和密码
      var name = this.name;
      var pwd = this.pwd;
      /* //2、创建正则表达式，用户名：字母。数字。下划线三到八位
      var regName = /^\w{3,8}$/;
        //密码：数字，三到八位
      var regPwd = /^\d{3,8}$/;
      //3、验证用户名：如果失败，提示错误信息
      if(regName.test(this.name)){
        this.nameMsg="用户名格式正确"
      }else{
        this.nameMsg="用户名3~8位字母数字下划线组成"
        // Toast("用户名不正确，请检查")
      }
      //4、验证密码：如果失败，提示错误信息
      if(regPwd.test(this.pwd)){
        this.pwdMsg="密码格式正确"
      }else{
        this.pwdMsg="密码3~8位数字"
        // Toast("密码不正确，请检查")
      } */
      //5、发送ajax请求  http://127.0.0.1:3000/login
      this.axios
        .get("http://127.0.0.1:3000/login", {
          params: {
            name,
            pwd
          }
        })
        .then(res => {
          // Toast(res.data.msg)
          if (res.data.code == 1) {
            alert("登陆成功");
            this.$router.push("/index")
          } else {
            alert("用户名或密码有误");
          }
        });
      //6、获取返回结果
      //7、提示，登陆成功或者用户名或密码有误
    }
  }
};
</script>
<style scoped>
.app-login{
  text-align: center;
  margin-top:10rem; 
}
</style>
