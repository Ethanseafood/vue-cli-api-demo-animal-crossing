<template>
  <button type="button" @click="numIncrease">click</button>
  <div v-for="item in imgArr" :key="item.id">
    <img :src="item.image_uri" alt="" />
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      imgArr: [],
    };
  },
  methods: {
    numIncrease() {
      const x = 1,
        y = 2;
      this.$emit("addNum", { x, y });
    },
  },
  emits: ["addNum"],
  mounted: async function () {
    try {
      const res = await axios("http://acnhapi.com/v1/fish/");
      // .then((res) => {
      this.imgArr = res.data;
      console.log(res);
      // });
    } catch (err) {
      console.log(err);
    }
  },
};
</script>
