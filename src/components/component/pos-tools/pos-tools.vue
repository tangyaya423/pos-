<template>
    <div class="pos-tool">
      <el-row class="pos-aside">
        <el-col :span='7' class="pos-order"  id="pos-order">
          <el-tabs>
            <el-tab-pane label='点餐'>
              <order></order>
            </el-tab-pane>
            <el-tab-pane label='挂单'>挂单</el-tab-pane>
            <el-tab-pane label='外卖'>外卖</el-tab-pane>
          </el-tabs>
        </el-col>
        <el-col class="pos-goods">
          <goods :oftenFoods="oftenFoods" :typeFoods="typeFoods"></goods>
        </el-col>
      </el-row>
    </div>
</template>

<script>
import Order from './components/order'
import Goods from '../goods/goods'
export default {
  name: 'posTools',
  props: ['oftenFoods','typeFoods'],
  components: {
    Order,
    Goods
  },
  mounted () {
    let orderHeight = document.body.clientHeight
    document.getElementById('pos-order').style.height = orderHeight + 'px'
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus" scoped>
.pos-aside
  top 0
  bottom 0
  display flex
  overflow hidden
  .pos-order
    background-color: #F9FAFC
    width 40%
    border-right 1px solid #C0CCDA
</style>
