<!--
 * @Author: ningbo.kang
 * @Date: 2019-11-14 11:31:19
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2019-11-14 16:00:53
 * @Description: 
 * ### Ellipsis-Text组件 *
使用场景：1.适用于单行文字超出显示省略号；2.适用于多行文本超出指定行显示省略号（或追加【更多】按钮）
* props：
[content-内容，line-默认标签数据，triggerMore-是否触发展开操作，hasMore-是否显示更多按钮，isHtml-是否html内容，revealWidth-更多按钮宽度，revealText-更多按钮文字，foldText-收起按钮文字]
* 事件：reveal（展开）、fold（收起）
-->
<template>
  <div :class="['vx-ellipsis-text']"
    :style="{ 'max-height': maxHeight }">
    <div class="ellipsis-content"
      :style="{ '-webkit-line-clamp': line }"
      ref="txtContent"
      v-html="content"
      v-if="isHtml"></div>
    <div class="ellipsis-content"
      :style="{ '-webkit-line-clamp': line }"
      ref="txtContent"
      v-else>{{ content | trimEnter }}</div>
  </div>
</template>

<script>
export default {
  filters: {
    trimEnter(data) {
      return data ? data.replace(/[\r\n]/g, "") : "";
    }
  },
  props: {
    /* 文字内容 */
    content: {
      type: String
      // default: '这是一段示例文字，用来测试的。这是一段示例文字，用来测试的。这是一段示例文字，用来测试的。这是一段示例文字，用来测试的。这是一段示例文字，用来测试的。这是一段示例文字，用来测试的。这是一段示例文字，用来测试的。'
    },
    /* 展示几行文字 */
    line: {
      type: [Number, String],
      default: 1
    },
    /* 是否是html内容 */
    isHtml: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      fontSize: 14, // 默认字号14px
      lineHeight: 22 // 默认行高22
    };
  },
  computed: {
    maxHeight() {
      return `${this.lineHeight * this.line}px`;
    }
  },
  mounted() {
    // this.$nextTick(() => {
    //   let txtEle = this.$refs.txtContent;
    //   if (txtEle.currentStyle) {
    //     this.fontSize = Number(txtEle.currentStyle.fontSize.replace('px', ''));
    //     this.lineHeight = Number(txtEle.currentStyle.lineHeight.replace('px', ''));
    //   } else {
    //     this.fontSize = Number(getComputedStyle(txtEle).fontSize.replace('px', ''));
    //     this.lineHeight = Number(getComputedStyle(txtEle).lineHeight.replace('px', ''));
    //   }
    // });
  }
};
</script>

<style lang="less" scoped>
/*
 * 行高 h
 * 字号 f
 * 最大行数 n
 * ...更多容器的宽 w
 */
.vx-ellipsis-text {
  @keyframes width-change {
    0%,
    100% {
      width: 100%;
    }
    50% {
      width: 30%;
    }
  }
  position: relative;
  width: 100%;
  max-height: 66px; /* h*n */
  line-height: 22px; /* h */
  overflow: hidden;
  color: #333;
  // animation: width-change 8s ease infinite;
  .ellipsis-container {
    position: relative;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 3; /* n */
    font-size: 70px; /* w */
    color: transparent;
    span {
      display: -webkit-box;
    }
  }
  .ellipsis-content {
    vertical-align: top;
    color: #333;
    // text-align: justify;
    display: -webkit-box;
    overflow: hidden;
    text-overflow: ellipsis;
    -webkit-box-orient: vertical;
    font-size: 14px; /* f */
    white-space: pre-wrap;
    &.more {
      display: inline;
    }
  }
  .ellipsis-ghost {
    position: absolute;
    z-index: 1;
    top: 0;
    left: 50%;
    width: 100%;
    height: 100%;
    color: #000;
    // background: rgba(255, 0, 0, 0.16);
  }
  .ellipsis-ghost:before {
    content: "";
    display: block;
    float: right;
    width: 50%;
    height: 100%;
  }
  .ellipsis-placeholder {
    content: "";
    display: block;
    float: right;
    width: 50%;
    height: 66px; /* h*n */
  }
  .ellipsis-more {
    float: right;
    text-align: right;
    font-size: 14px; /* f */
    width: 70px; /* w */
    height: 22px; /* h */
    margin-top: -22px; /* -h */
    cursor: pointer;
    color: #3a62f4;
    &.html {
      padding-left: 20px;
      background: linear-gradient(to left, #fff0 15%, #fff 46%);
    }
  }
  .ellipsis-fold-text {
    position: relative;
    z-index: 5;
    cursor: pointer;
    // text-align: right;
    font-size: 14px;
    color: #3a62f4;
  }
  &.reveal {
    max-height: auto !important;
    .ellipsis-container {
      display: block !important;
    }
  }
}
</style>
