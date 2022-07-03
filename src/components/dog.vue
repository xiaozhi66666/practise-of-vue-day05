<template>
  <div>
    <div class="dog">
      <img
        src="https://scpic.chinaz.net/files/pic/pic9/202003/zzpic23514.jpg"
        alt=""
      />
      <h4 class="text">我是一只可爱又迷人的小狗</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: "Vuedemo05Dog",

  data() {
    return {};
  },

  mounted() {},

  methods: {},
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
}
.text {
  font-size: 30px;
  color: pink;
}
</style>