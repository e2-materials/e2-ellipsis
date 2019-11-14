<!--
 * @Author: ningbo.kang
 * @Date: 2019-11-14 09:20:26
 * @LastEditors: ningbo.kang
 * @LastEditTime: 2019-11-14 09:39:54
 * @Description: 
 -->
<template >
 <div>

   <e2-ellipsis tooltip={true}>{{ text }}</e2-ellipsis>
 </div>
</template>

<script>
  import e2Ellipsis from '../src'

  export default {
    name: 'App',
    components: { e2Ellipsis },

    data () {
      return { text: 'hello-world(emoji="🤔")' }
    }
  }
</script>

<style lang="scss">
  .docs {
    width: 50%;
    margin: auto;
    padding: 10px;
  }

  code {
    margin-top: 20px;
    padding: 10px;
    border-radius: 5px;
    background: #3d3d3d;
    color: #f3f3fe;
  }
</style>
