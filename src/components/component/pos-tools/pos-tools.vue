<template>
    <div class="pos-tool">
      <el-row class="pos-aside">
        <el-col :span='7' class="pos-order"  id="pos-order">
          <el-tabs>
            <el-tab-pane label='点餐'>
               <el-table id="table-box" border :data="tableData">
                <el-table-column prop="goodsId" v-if="no"></el-table-column>
                <el-table-column prop="goodName" label='商品名称'></el-table-column>
                <el-table-column prop="count" label='数量'></el-table-column>
                <el-table-column prop="price"  label='金额'></el-table-column>
                <el-table-column width="150px" fixed="right" label='操作' type="index">
                  <template>
                    <el-button type="primary" plain size="mini" @click="delt()">删除</el-button>
                    <el-button type="primary" plain size="mini" @click="addBtn(goodsId)">增加</el-button>
                  </template>
                </el-table-column>
              </el-table>
              <div class="total">
                <p>
                  <small>数量：{{totalCount}}</small>
                  <small style="margin-left:30px;">金额：{{totalMoney}}</small>元
                </p>
              </div>
              <div class="operate-btn">
                <el-button type="warning" size="small">挂单</el-button>
                <el-button type="danger" size="small" @click="deltAll">删除</el-button>
                <el-button type="success" size="small" @click="check">结账</el-button>
              </div>
            </el-tab-pane>
            <el-tab-pane label='挂单'>挂单</el-tab-pane>
            <el-tab-pane label='外卖'>外卖</el-tab-pane>
          </el-tabs>
        </el-col>
        <el-col class="pos-goods">
          <goods
          :oftenFoods="oftenFoods"
          :typeFoods="typeFoods"
          :tableData="tableData"
          @addGoods="add"
          @totalc="addc"
          @totalm="addm"
          ></goods>
        </el-col>
      </el-row>
    </div>
</template>

<script>
import Order from './components/order'
import Goods from '../goods/goods'
export default {
  name: 'posTools',
  props: ['oftenFoods', 'typeFoods'],
  data () {
    return {
      tableData: [],
      no: false,
      ind: [],
      totalCount: 0,
      totalMoney: 0
    }
  },
  components: {
    Order,
    Goods
  },
  methods: {
    add (msg) {
      this.tableData = msg
    },
    addc (c) {
      this.totalCount = c
    },
    addm (m) {
      this.totalMoney = m
    },
    addBtn (tableData) {
      this.tableData.forEach(element => {
        if (element.goodsId === this.tableData.goodsId) {
          console.log(this.tableData.goodsId)
          element.count++
        }
      })
    },
    delt (tableData) {
      for (let i = 0; i < this.tableData.length; i++) {
        if (this.tableData[i].count === 1) {
          this.tableData.splice(i, 1)
        } else {
          if (this.tableData[i].goodsId === 1) {
            this.tableData[i].count--
          }
        }
      }
    },
    deltAll () {
      this.tableData = []
      this.totalCount = ''
      this.totalMoney = ''
    },
    check () {
      if (this.totalMoney == 0) {
        this.$message.error('请勿空结，老板了解你急切的心情！')
      } else{
        this.$message.success('真棒，你又为小店壮大贡献了一份力量！')
        this.deltAll()
      }
    }
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
      .operate-btn
      text-align center
      margin-top 20px
      .total p
        text-align center
</style>
