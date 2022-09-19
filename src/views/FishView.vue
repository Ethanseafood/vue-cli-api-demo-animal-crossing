<template>
  {{ num }}
  <FishList @addNum="callBack" />
</template>

<script>
import FishList from "@/components/FishList.vue";
export default {
  data() {
    return {
      num: 0,
    };
  },
  components: {
    FishList,
  },
  methods: {
    callBack(n) {
      this.num += n.y;
    },
  },
};
</script>
