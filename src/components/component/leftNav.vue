<template>
  <div class="leftNav">
    <ul class="leftNav-swaper">
      <li class="swaper">
        <i class="icon iconfont icon-goumai"></i>
        <div class="icon-desc">收银</div>
      </li>
      <li class="swaper">
        <i class="icon iconfont icon-dianpu"></i>
        <div class="icon-desc">商铺</div>
      </li>
      <li class="swaper">
        <i class="icon iconfont icon-shangpin-tianchong"></i>
        <div class="icon-desc">商品</div>
      </li>
      <li class="swaper">
        <i class="icon iconfont icon-shezhi"></i>
        <div class="icon-desc">会员</div>
      </li>
      <li class="swaper">
        <i class="icon iconfont icon-fenqigou"></i>
        <div class="icon-desc">统计</div>
      </li>
      <li class="swaper">
        <i class="icon iconfont icon-zuanshi"></i>
        <div class="icon-desc">设置</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'leftnav'
}
</script>

<style lang="stylus" scoped>
.leftNav
  display flex
  float left
  height 100%
  background #1D8ce0
  border 1px solid red
  .leftNav-swaper
    padding 0
    margin 0
    .swaper
      list-style none
      text-align center
      color #fff
      padding 20px
      border-bottom 1px solid #20a0ff
      .icon
        font-size 26px
      .icon-desc
        padding-top 10px
</style>
