<template>
  <div>
    <div class="celan">
      <my-leftlan></my-leftlan>
    </div>
    <my-header></my-header>
    <div class="container">
      <h3>笔记本商品列表</h3>
      <div class="table">
        <table>
          <tr>
            <th>
              <input type="checkbox">
              <span>全选</span>
            </th>
            <th>编号</th>
            <th>型号</th>
            <th>主标题</th>
            <th>规格</th>
            <th>单价</th>
            <th>操作</th>
          </tr>
          <tr v-for="item of list" :key="item.lid">
            <td>
              <input type="checkbox">
            </td>
            <td v-text="item.lid"></td>
            <td v-text="item.lname"></td>
            <td v-text="item.title"></td>
            <td v-text="item.spec"></td>
            <td v-text="'￥'+item.price"></td>
            <td>
              <span>详情</span>
              <span>修改</span>
              <span>删除</span>
            </td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>
<script>
import myLeftlan from "@/components/leftlan.vue";
import myHeader from "@/components/header.vue";
export default {
  data() {
    return {
      list: []
    };
  },
  created() {
    this.getList();
  },
  methods: {
    getList() {
      var url = "http://127.0.0.1:3000/getList";
      this.axios.get(url).then(result => {
        console.log(result.data);
        this.list = result.data;
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
}
table {
  border-collapse: collapse;
}
table th {
  border-bottom: 2px solid #ddd;
  text-align: left;
  padding: 1rem;

}
table td {
  border-bottom: 1px solid #ddd;
  width: 10%;
  text-align: left;
  padding: 1rem;
}
</style>
