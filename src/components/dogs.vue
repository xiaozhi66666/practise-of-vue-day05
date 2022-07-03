<template>
  <div>
    <div class="dog">
      <img :src="obj.dogImgUrl" alt="" />
      <h4 class="text">{{ obj.dogName }}</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: "Vuedemo05Dog",
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
  height: 80%;
}
.text {
  font-size: 30px;
  color: pink;
}
</style>