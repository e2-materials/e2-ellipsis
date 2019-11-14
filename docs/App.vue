<!--
 * @Author: ningbo.kang
 * @Date: 2019-11-14 09:20:26
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2019-11-14 16:11:22
 * @Description: 
 -->
<template>
  <div style="margin:0 auto;background-color:#099;width:600px;">
    <div>
      <e2-ellipsis :tooltip="false"
        line="1">{{ text }}</e2-ellipsis>
    </div>
    <div>
      <e2-ellipsis line="1">{{ text }}</e2-ellipsis>
    </div>
    <div style="background-color:#ccc;width:400px;">
      <e2-ellipsis :tooltip="true"
        line="2">这里是官方的 Vue 特有代码的风格指南。如果在工程中使用 Vue，为了回避错误、小纠结和反模式，该指南是份不错的参考。不过我们也不确信风格指南的所有内容对于所有的团队或工程都是理想的。所以根据过去的经验、周围的技术栈、个人价值观做出有意义的偏差是可取的。
      </e2-ellipsis>
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
    return {
      text:
        "特有代码的风格指南。如果在工程中使用。如果在工程中使用 Vue，为了回避错误、小纠结和反模式，该指南是份不错的参考"
    };
  }
};
</script>
