<!--
 * @Author: ningbo.kang
 * @Date: 2019-09-26 10:16:53
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2019-11-14 16:10:17
 * @Description:
 -->
<script>
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
    }
  },
  methods: {
    getStrDom(fullStr, line) {
      return (
        <div title={fullStr}>
          <EllipsisText line={line} content={fullStr} />
        </div>
      );
    },
    getTooltip(fullStr, line) {
      return (
        <Tooltip>
          <template slot="title">{fullStr}</template>
          <div>
            <EllipsisText line={line} content={fullStr} />
          </div>
        </Tooltip>
      );
    }
  },
  render() {
    const { tooltip, line } = this.$props;
    const str = this.$slots.default.map(vNode => vNode.text).join("");
    const strDom = tooltip
      ? this.getTooltip(str, line)
      : this.getStrDom(str, line);
    return strDom;
  }
};
</script>
