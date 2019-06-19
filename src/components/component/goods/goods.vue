<template>
  <div>
    <div class="goods-offen">
      <div class="goods-title">常用商品</div>
      <ul>
        <li
        v-for="goods in oftenFoods"
        :key="goods.goodsId"
        @click="addFoods(goods)"
        style="list-style:none;padding:10px 20px;
    background:#F2F6FC;float:left;width:16%;margin-left:20px;text-align:center;border-radius:5px;margin-top:20px;cursor:pointer;">
          <span>{{goods.goodsName}}</span>
          <span style="color:#409EFF;">{{goods.price}}元</span>
        </li>
      </ul>
    </div>
    <div class="goods-type">
      <el-tabs >
        <el-tab-pane label="汉堡">
          <div>
            <ul class="cookList">
              <li v-for="goods in typeFoods" :key="goods.goodsId" @click="addFoods(goods)">
                <span class="foodImg">
                  <img :src="goods.goodsImg" width="100%" height="70%">
                </span>
                <span class="foodName">{{goods.goodsName}}</span>
                <span class="foodPrice">￥{{goods.price}}元</span>
              </li>
            </ul>
          </div>
        </el-tab-pane>
        <el-tab-pane label="小食"></el-tab-pane>
        <el-tab-pane label="饮料"></el-tab-pane>
        <el-tab-pane label="套餐"></el-tab-pane>
      </el-tabs>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Goods',
  props: ['oftenFoods', 'typeFoods', 'tableData'],
  data () {
    return {
      tableData: [],
      totalCount: 0,
      totalMoney: 0
    }
  },
  methods: {
    addFoods (goods) {
      // 判断是否已存在于订单中
      let had = false
      for (let i = 0; i < this.tableData.length; i++) {
        if (this.tableData[i].goodsId === goods.goodsId) {
          had = true
        }
      }
      // 针对不同结果进行操作
      if (had) {
        let arr = this.tableData.filter(a => a.goodsId === goods.goodsId)
        arr[0].count++
      } else {
        let newData = {goodsId: goods.goodsId, goodName: goods.goodsName, price: goods.price, count: 1}
        this.tableData.push(newData)
        this.$emit('addGoods', this.tableData)
      }
      this.total()
    },
     total () {
       this.totalCount = 0
       this.totalMoney = 0
      this.tableData.forEach(element => {
        this.totalCount += element.count
        this.totalMoney = this.totalMoney + (element.count * element.price)
        this.$emit('totalc', this.totalCount)
        this.$emit('totalm', this.totalMoney)
      })
      // this.total()
    }
  }
}
</script>
<style lang="stylus" scoped>
  .goods-title
    text-align center
.goods-type
  clear both
  .cookList li
    list-style: none
    width: 18%
    border: 1px solid #E5E9F2
    height: auot
    overflow: hidden
    background-color: #fff
    padding: 2px
    float: left
    cursor: pointer
    text-align center
    margin-left 20px
    .cookList li span
      display: block
      float: left
    .foodName
      display block
      font-size: 15px
      padding-left: 10px
      color: brown
    .foodPrice
      font-size: 14px
      padding-left: 10px
      padding-top: 10px
</style>
