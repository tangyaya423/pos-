<template>
  <div>
    <leftnav></leftnav>
    <pos-tools :oftenFoods="oftenFoods" :typeFoods="typeFoods"></pos-tools>
  </div>
</template>

<script>
import leftnav from './component/leftNav'
import posTools from './component/pos-tools/pos-tools'
import axios from 'axios'
export default {
  name: 'pos',
  data () {
    return {
      oftenFoods: [],
      typeFoods: []
    }
  },
  components: {
    leftnav,
    posTools
  },
  created () {
    axios.get('api/oftenFoods.json').then(response => {
      // console.log(response)
      this.oftenFoods = response.data
    }).catch(error => {
      console.log(error)
    })

    axios.get('api/typeFoods.json').then(response => {
      // console.log(response)
      this.typeFoods = response.data
    }).catch(error => {
      console.log(error)
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus" scoped>
</style>
