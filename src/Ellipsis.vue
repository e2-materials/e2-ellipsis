<!--
 * @Author: ningbo.kang
 * @Date: 2019-09-26 10:16:53
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2019-11-14 16:44:42
 * @Description:
 -->
<script>
import { cutStrByFullLength, getStrFullLength } from "./util";
import Tooltip from "ant-design-vue/es/tooltip";
import EllipsisText from "./EllipsisText.vue";

export default {
  name: "e2-ellipsis",
  components: {
    Tooltip,
    EllipsisText
  },
  props: {
    tooltip: {
      type: Boolean,
      default: true
    },
    line: {
      type: [Number, String],
      default: 1
    },
    length: {
      type: Number,
      default: 0
    }
  },
  methods: {
    getStrDom(fullStr, line, fullLength) {
      if (this.length) {
        const cutStr =
          cutStrByFullLength(fullStr, this.length) +
          (fullLength > this.length ? "..." : "");
        return <div title={fullStr}>{cutStr}</div>;
      } else {
        return (
          <div title={fullStr}>
            <EllipsisText line={line} content={fullStr} />
          </div>
        );
      }
    },
    getTooltip(fullStr, line, fullLength) {
      if (this.length) {
        const cutStr =
          cutStrByFullLength(fullStr, this.length) +
          (fullLength > this.length ? "..." : "");
        return (
          <Tooltip>
            <template slot="title">{fullStr}</template>
            <div>{cutStr}</div>
          </Tooltip>
        );
      } else {
        return (
          <Tooltip>
            <template slot="title">{fullStr}</template>
            <div>
              <EllipsisText line={line} content={fullStr} />
            </div>
          </Tooltip>
        );
      }
    }
  },
  render() {
    const { tooltip, line } = this.$props;
    const str = this.$slots.default.map(vNode => vNode.text).join("");
    const fullLength = getStrFullLength(str);
    const strDom = tooltip
      ? this.getTooltip(str, line, fullLength)
      : this.getStrDom(str, line, fullLength);
    return strDom;
  }
};
</script>
