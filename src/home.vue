<template>
  <div class="home">
    <div class="btn-show">
      <ui-button
        @click="handleClick"
        :large="size === 'large'"
        :xlarge="size === 'xlarge'"
        :small="size === 'small'"
        :xsmall="size === 'xsmall'"
        :tile="style === 'tile'"
        :rounded="style === 'rounded'"
        :circle="style === 'circle'"
        :disabled="disabled"
      >winnic</ui-button>
    </div>
    <div class="btn-container">
      <ui-button @click="onClick('xlarge')" xlarge color="green">超大</ui-button>
      <ui-button @click="onClick('large')" large color="yellow">大</ui-button>
      <ui-button @click="onClick('')" :color="`rgba(87,67,12,1)`">winnic</ui-button>
      <ui-button @click="onClick('small')" small>小</ui-button>
      <ui-button @click="onClick('xsmall')" xsmall>超小</ui-button>
    </div>
    <div class="btn-container">
      <ui-button @click="changeRadius('')">正常</ui-button>
      <ui-button @click="changeRadius('tile')" tile>直角</ui-button>
      <ui-button @click="changeRadius('rounded')" rounded>半圆</ui-button>
      <ui-button @click="changeRadius('circle')" circle>圆</ui-button>
      <ui-button @click="handleDisable()" disabled>禁用</ui-button>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
import UiButton from "@/components/ui/uiButton.vue";
@Component({
  components: {
    UiButton
  }
})
export default class Home extends Vue {
  private size = "";
  private style = "";
  private disabled = false;
  private onClick(ev: string) {
    this.size = ev;
  }
  private changeRadius(name: string) {
    this.style = name;
  }
  private handleDisable() {
    this.disabled = !this.disabled;
  }
  private handleClick(event: MouseEvent) {
    console.log(event);
  }
}
</script>


<style lang="stylus" scoped>
.btn-show
  width: 480px
  height: 160px
  display: flex
  justify-content: center
  align-items: center
.btn-container
  margin-top: 10px
  .ui-button
    margin-right: 5px
</style>
