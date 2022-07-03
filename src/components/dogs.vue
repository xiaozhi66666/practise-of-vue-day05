<template>
  <div>
    <div class="dog" v-for="(item, index) in arr" :key="index">
      <img :src="item.dogImgUrl" alt="" @click="select(index)" />
      <div
        class="text"
        @click="select(index)"
        ref="dog"
        :style="{ backgroundColor: color }"
      >
        {{ item.dogName }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Vuedemo05Dog",
  props: ["arr"],
  data() {
    return {
      color: "",
      isShow: "",
    };
  },

  mounted() {},

  methods: {
    select(index) {
      this.isShow = index;
      this.$refs.dog.forEach((item) => (item.style.backgroundColor = ""));
      this.$refs.dog[index].style.backgroundColor = `rgb(${Math.floor(
        Math.random() * 256
      )}, ${Math.floor(Math.random() * 256)}, ${Math.floor(
        Math.random() * 256
      )})`;
      // console.log(this.arr[index].$refs.dog);
      // this.arr[index].$refs.backgroundColor = `rgb(${Math.floor(
      //   Math.random() * 256
      // )}, ${Math.floor(Math.random() * 256)}, ${Math.floor(
      //   Math.random() * 256
      // )})`;
      // // this.arr[index].$refs.backgroundColor = `rgb(${Math.floor(
      //   Math.random() * 256
      // )},${Math.floor(Math.random() * 256)},${Math.floor(
      //   Math.random() * 256
      // )})`)
      // .color = `rgb(${Math.floor(
      //   Math.random() * 256
      // )},${Math.floor(Math.random() * 256)},${Math.floor(
      //   Math.random() * 256
      // )})`
      this.$emit("select", this.arr[index].dogName);
    },
  },
};
</script>

<style  scoped>
.dog {
  width: 400px;
  height: 400px;
  border: 6px solid black;
  margin-right: 10px;
  text-align: center;
  float: left;
}
img {
  width: 100%;
  height: 80%;
}
.text {
  font-size: 30px;
  color: pink;
}
</style>