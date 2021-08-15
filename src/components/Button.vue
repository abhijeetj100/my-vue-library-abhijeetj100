<template>
  <div>
    <button @click="click">
        <slot></slot>
    </button>
  </div>
</template>
<script lang="ts">
import { Component, Prop, Vue, Emit } from 'vue-property-decorator'

@Component
export default class Button extends Vue {
    @Emit()
  public click () {}
}
</script>

<style lang="scss" scoped>

</style>
