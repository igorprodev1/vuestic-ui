<template>
  <div
    class="va-card__content"
    :style="contentStyles"
  >
    <slot />
  </div>
</template>

<script lang="ts">
import { Component, Mixins } from 'vue-property-decorator'

import { makeContextablePropsMixin } from '../../context-test/context-provide/ContextPlugin'
import { getColor } from '../../../services/ColorThemePlugin'

const CardContentPropsMixin = makeContextablePropsMixin({
  textColor: { type: String, default: '' },
})

@Component({
  name: 'VaCardContent',
})
export default class VaCardContent extends Mixins(
  CardContentPropsMixin,
) {
  get contentStyles () {
    return {
      color: getColor(this, this.c_textColor),
    }
  }
}
</script>
