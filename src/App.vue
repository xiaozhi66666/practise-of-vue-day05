<template>
  <div id="all">
    <table border="1" width="700" style="border-collapse: collapse">
      <caption>
        购物车
      </caption>
      <thead>
        <tr>
          <th><input type="checkbox" v-model="isAll" /> <span>全选</span></th>
          <th>名称</th>
          <th>价格</th>
          <th>数量</th>
          <th>总价</th>
          <th>操作</th>
        </tr>
      </thead>
      <tbody>
        <Tr
          v-for="(obj, index) in goodList"
          :key="index"
          :obj="obj"
          @isSelect="isSelectFn"
        ></Tr>
      </tbody>
      <tfoot>
        <tr v-if="goodList.length !== 0">
          <td>合计:</td>
          <td colspan="5">{{ allPrice }}</td>
        </tr>
        <tr v-else class="over">
          <td colspan="6">"抱歉！已经没有任何数据了"</td>
        </tr>
      </tfoot>
    </table>
  </div>
</template>


<script>
import Tr from "@/components/Tr.vue";

export default {
  components: { Tr },
  data() {
    return {
      goodList: [
        {
          name: "诸葛亮",
          price: 1000,
          num: 0,
          checked: false,
        },
        {
          name: "蔡文姬",
          price: 1500,
          num: 0,
          checked: false,
        },
        {
          name: "妲己",
          price: 2000,
          num: 0,
          checked: false,
        },
        {
          name: "鲁班",
          price: 2200,
          num: 0,
          checked: false,
        },
      ],
    };
  },
  computed: {
    isAll: {
      set(val) {
        this.goodList.forEach((item) => {
          item.checked = val;
        });
      },
      get() {
        return this.goodList.length == 0
          ? false
          : this.goodList.every((item) => item.checked == true);
      },
    },
    allPrice() {
      const arr = this.goodList.filter((item) => item.checked);
      return arr.reduce((sum, item) => (sum += item.num * item.price), 0);
    },
  },
  methods: {
    isSelectFn(name) {
      const index = this.goodList.findIndex((item) => item.name == name);
      this.goodList.splice(index, 1);
    },
  },
};
</script>

<style>
#all {
  margin-left: 50%;
  transform: translateX(-50%);
}
table {
  text-align: center;
}
.over {
  height: 100px;
}
</style>