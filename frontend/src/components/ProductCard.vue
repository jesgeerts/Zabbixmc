<!--
  - Copyright (c) 2021 Loper.me <bizrenay@gmail.com>
  -
  - Licensed under the Apache License, Version 2.0 (the "License");
  - you may not use this file except in compliance with the License.
  - You may obtain a copy of the License at
  -
  -     http://www.apache.org/licenses/LICENSE-2.0
  -
  - Unless required by applicable law or agreed to in writing, software
  - distributed under the License is distributed on an "AS IS" BASIS,
  - WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  - See the License for the specific language governing permissions and
  - limitations under the License.
  -->

<template>
  <Card class="product-card">
    <div class="product-card__title">
      {{ title }}
    </div>
    <slot />
  </Card>
</template>

<script lang="ts">
import {Component, Prop, Vue} from 'vue-property-decorator'
import Card from './Card.vue'

@Component({
  components: {
    Card
  }
})
export default class extends Vue {
  @Prop() public title!: string;
}
</script>

<style lang="stylus" scoped>
@import '~@/styles/common.styl'

.product-card > img
  @extend .disable-highlight
.product-card
  background-image linear-gradient(to right bottom, #e0e0ef, #f5f5fd)
  transition blur .3s, ease-out .25s
  box-shadow 10px 10px 30px #e4e4f2
  border-radius 3px 15px 0 15px
  background-repeat no-repeat
  background-position center
  padding 0

  &:hover
    cursor pointer
    filter blur(1px)
    transform matrix(1, 0, 0, 1, 0, -5)

  &:hover img
    transform scale(1.1)

  > img
    z-index 0
    pointer-events none
    transition all .2s
    position relative
    text-align center

  &__title
    padding 30px
    font-family AcromBold, sans-serif
    font-weight 700
    max-height 75px
    color #0f0f0f
    width 100%
</style>
