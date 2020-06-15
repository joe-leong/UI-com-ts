<template>
    <!-- <button class="ui-button" v-on="$listeners">
      12
    </button>-->
    <button
        class="ui-button"
        :class="{large,xlarge,small,xsmall,tile,circle,rounded,disabled}"
        :style="`--color-tint:${tintColor}`"
        @click="handleClick"
    >
        <slot>Button</slot>
    </button>
</template>

<script lang='ts'>
import { Component, Vue, Emit, Prop } from "vue-property-decorator";
@Component
export default class UIButton extends Vue {
  @Prop(Boolean)
  private xsmall: boolean | undefined;

  @Prop(Boolean)
  private small: boolean | undefined;

  @Prop(Boolean)
  private large: boolean | undefined;

  @Prop(Boolean)
  private xlarge: boolean | undefined;

  @Prop(Boolean)
  private tile: boolean | undefined;

  @Prop(Boolean)
  private rounded: boolean | undefined;

  @Prop(Boolean)
  private circle: boolean | undefined;

  @Prop(Boolean)
  private disabled: boolean | undefined;

  @Prop(String)
  private color: string | undefined;

  @Emit("click")
  private clickEvent(event: MouseEvent) {
    return event;
  }
  private handleClick(event: MouseEvent) {
    !this.disabled && this.clickEvent(event);
  }

  private get tintColor() {
    return this.color || `#2D8CF0`;
  }
}
</script>

<style lang="stylus">
resize(minWidth, height, paddingLR, fontSize)
    min-width: minWidth
    height: height
    padding: 0 paddingLR
    font-size: fontSize
    &.rounded, &.circle
        border-radius: (@height / 2)
    &.circle
        width: @height
        min-width: 0
        padding: 0
.ui-button
    min-width: 64px
    height: 36px
    border: 0 solid black
    border-radius: 4px
    font-size: 0.875rem
    font-weight: 500
    letter-spacing: 0.09em
    color: #17233D
    background-color: var(--color-tint, #2D8CF0)
    outline: none
    cursor: pointer
    user-select: none
    &:hover
        filter: brightness(120%)
    &:active
        filter: brightness(80%)
    &.large
        resize(78px, 44px, 19px, 0.875rem)
    &.xlarge
        resize(92px, 52px, 23px, 1rem)
    &.small
        resize(50px, 28px, 12px, 0.75rem)
    &.xsmall
        resize(36px, 20px, 9px, 0.625rem)
    &.tile
        border-radius: 0
    &.rounded, &.circle
        border-radius: (@height / 2)
    &.circle
        width: @height
        min-width: 0
        padding: 0
    &.disabled
        background-color: #f5f5f5
        color: #c5c8ce
        cursor: not-allowed
</style>