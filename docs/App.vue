<!--
 * @Author: ningbo.kang
 * @Date: 2019-11-14 09:20:26
 * @LastEditors: ningbo.kang
 * @LastEditTime: 2019-11-14 10:57:44
 * @Description: 
 -->
<template>
  <div>
    <div>
      <e2-ellipsis :tooltip="true">{{ text }}</e2-ellipsis>
    </div>
    <div style="background-color:#ccc">
      <e2-ellipsis :tooltip="true">这是一个很长的测试文字，会有省略号</e2-ellipsis>
    </div>
  </div>
</template>

<script>
import e2Ellipsis from "../src";
import "ant-design-vue/dist/antd.css";

export default {
  name: "App",
  components: { e2Ellipsis },
  data() {
    return { text: "hello-world" };
  }
};
</script>
