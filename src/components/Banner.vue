<template>
  <div class="banner" :style="bannerStyles" :class="`banner__${position}`">
    <slot></slot>
  </div>
</template>
<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component
export default class Banner extends Vue {
  @Prop({ type: String, default: 'top', validator: (position) => ['top', 'bottom'].indexOf(position) > -1 }) public position!: string;
  @Prop({ type: Object, default: () => {} }) public styles!: Object;

  get bannerStyles () {
    return {
      ...defaultStyles,
      ...this.styles
    }
  }
}

const defaultStyles = {
  left: 0,
  right: 0
}
// export default {
//   props: {
//     position: {
//       type: String,
//       default: 'top',
//       validator(position) {
//         return ['top', 'bottom'].indexOf(position) > -1;
//       },
//     },
//     styles: {
//       type: Object,
//       default: () => ({}),
//     },
//   },
//   data() {
//     return {
//       bannerStyles: {
//         ...defaultStyles,
//         ...this.styles,
//       },
//     };
//   },
// };
</script>

<style lang="scss" scoped>
.banner {
  padding: 12px;
  background-color: #fcf6cd;
  color: #f6a623;
  text-align: left;
  position: fixed;
  z-index: 2;
}
.banner__top {
  top: 0;
}
.banner__bottom {
  bottom: 0;
}
</style>
