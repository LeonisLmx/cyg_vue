<template>
  <div class="CopClass">
    <h1>{{msg}}</h1>
    <el-button type="primary" @click="login">show Channels</el-button>
    <el-table :data="channel_data" border justify="center" style="width: 100%">
      <el-table-column prop="name" label="Name"></el-table-column>
      <el-table-column prop="fex" label="Fex"></el-table-column>
      <el-table-column prop="legal" label="legal"></el-table-column>
      <el-table-column prop="scale" label="scale"></el-table-column>
      <el-table-column prop="depositEnabled" label="depositEnabled"></el-table-column>
      <el-table-column prop="meta" label="meta"></el-table-column>
      <el-table-column prop="tokenDecimals" label="tokenDecimals"></el-table-column>
      <el-table-column prop="withdrawEnabled" label="withdrawEnabled"></el-table-column>
    </el-table>
  </div>
</template>

<script>
import Vue from 'vue'
export default {
  name: 'CopName',
  data () {
    return {
      msg: 'Welcome to More DashBord!',
      checked: true,
      channel_data: []
    }
  },
  methods: {
    login: function () {
      var url = 'https://api-test.matrix.co/v1/market/trades'
      Vue.axios.get(url).then((response) => {
        this.channel_data = response.data.data.currencies
        // eslint-disable-next-line no-undef
        console.log('responses:' + response.data.data.currencies)
      }).catch((error) => {
        console.log('error!' + error)
      })
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
