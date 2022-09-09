<template>
  <div class="container">
    <select v-model="selected">
      <option disabled value="">Please select district</option>
      <option>大安區</option>
      <option>中正區</option>
      <option>松山區</option>
      <option>信義區</option>
      <option>萬華區</option>
      <option>中山區</option>
      <option>大同區</option>
      <option>士林區</option>
      <option>文山區</option>
      <option>內湖區</option>
      <option>南港區</option>
      <option>北投區</option>
      <option>臺大專區</option>
      <option>臺大公館校區</option>
    </select>

    <div>
      <table>
        <tr>
          <th>No.</th>
          <th>District</th>
          <th>Name</th>
        </tr>
        <tr v-for="item in bikeArr" :key="item.id">
          <template v-if="item.sarea == selected">
            <td>{{ item.sno }}</td>
            <td>{{ item.sarea }}</td>
            <td>{{ item.sna }}</td>
          </template>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      bikeArr: [],
      selected: "",
    };
  },
  methods: {},
  mounted: async function () {
    try {
      const res = await axios(
        "https://tcgbusfs.blob.core.windows.net/dotapp/youbike/v2/youbike_immediate.json"
      );
      // .then((res) => {
      this.bikeArr = res.data;
      console.log(res);
    } catch (err) {
      console.log(err);
    }

    // });
  },
};
</script>
<style scoped>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td,
th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>
