<template>
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
</template>

<script>
export default {
  name: "BikeList",
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
