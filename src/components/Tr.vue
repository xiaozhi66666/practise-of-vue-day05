<template>
  <tr>
    <th>
      <input type="checkbox" v-model="obj.checked" /><span> 是否购买 </span>
    </th>
    <td>{{ obj.name }}</td>
    <td>{{ obj.price }}</td>
    <td>
      <button @click="obj.num--" :disabled="obj.num == 0">-1</button
      ><input type="text" v-model="obj.num" @focus="fn" ref="count" /><button
        @click="obj.num++"
      >
        +1
      </button>
    </td>
    <td>{{ obj.price * obj.num }}</td>
    <td><a href="javascript:;" @click="delFn(obj.name)">删除</a></td>
  </tr>
</template>

<script>
export default {
  name: "Vuedemo05Tr",
  props: {
    obj: {
      type: Object,
      default: () => {
        return {};
      },
    },
  },
  data() {
    return {};
  },

  mounted() {},
  watch: {
    obj: {
      handler(val) {
        this.obj.num = this.obj.num <= 0 ? 0 : (this.obj.num = val.num);
      },
      deep: true,
    },
  },
  methods: {
    fn() {
      this.obj.num === 0 ? (this.$refs.count.value = "") : "";
    },
    delFn(name) {
      this.$emit("isSelect", name);
    },
  },
};
</script>

<style scoped>
</style>