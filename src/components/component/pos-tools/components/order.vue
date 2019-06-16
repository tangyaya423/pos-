<template>
  <div>
    <el-table border :data="tableData">
      <el-table-column prop="goodsname" label='商品名称'></el-table-column>
      <el-table-column prop="count" label='数量'></el-table-column>
      <el-table-column prop="price"  label='金额'></el-table-column>
      <el-table-column width="150px" fixed="right" label='操作'>
        <el-button type="primary" plain size="mini">删除</el-button>
        <el-button type="primary" plain size="mini">增加</el-button>
      </el-table-column>
    </el-table>
    <div class="total">
      <p>
        <small>数量：</small>
        <small style="margin-left:30px;">金额：</small>元
      </p>
    </div>
    <div class="operate-btn">
      <el-button type="warning" size="small">挂单</el-button>
      <el-button type="danger" size="small">删除</el-button>
      <el-button type="success" size="small">结账</el-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Order',
  props: [],
  data () {
    return {
      tableData: []
    }
  }
}
</script>
<style lang="stylus" scoped>
.operate-btn
  text-align center
  margin-top 20px
  .total p
    text-align center
</style>
