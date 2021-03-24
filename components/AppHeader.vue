<template lang="pug">
  header.header
    .header__content
      .header__controls
        h1.ttl Найдется все
        p Самые важные вещи для качественной жизни. Ласковые коты, вкусные&nbsp;
          | помидоры и умопомрачительные носки!
        category-picker(@categoryPicked="(category) => $emit('categoryPicked', category)")
      .header__creative
        .quarter-circle-blue
        .quarter-circle-green
        .half-circle-pink
        img.cat-1(src="/img/cat1.svg")
        img.cat-2(src="/img/cat2.svg")
        img.tomatoes-1(src="/img/tomatoes1.svg")
        img.tomatoes-2(src="/img/tomatoes2.svg")
        img.lines(src="/img/lines.svg")
        img.shoes(src="/img/shoes.svg")
        .dots
          div(v-for="i in 5" :key="i")
            span(v-for="j in 5" :key="j")
</template>

<script>
import CategoryPicker from '~/components/CategoryPicker'
export default {
  name: 'AppHeader',
  components: { CategoryPicker },
}
</script>

<style lang="sass" scoped>
.header
  background: #18191F
  color: #ffffff
  padding: 9.9375rem 0 11rem
  @media screen and (max-width: 768px)
    height: 100vh
    padding-top: 5rem
  &__content
    max-width: 75rem
    min-width: 320px
    margin: 0 auto
    display: flex
  &__controls
    flex: 1
    h1
      font-style: normal
      font-weight: 800
      font-size: 4.5rem
      line-height: 126%
      font-feature-settings: 'liga' off
    p
      margin: 3.125rem 0
      line-height: 178%
      font-feature-settings: 'liga' off
    @media screen and (max-width: 1200px)
      padding-left: 1rem
    @media screen and (max-width: 900px)
      padding: 0 1rem
      h1
        font-size: 3.5rem
        //font-weight: 600
  &__creative
    width: 31.8125rem
    height: 1px
    margin-bottom: -11rem
    align-self: flex-end
    position: relative
    @media screen and (max-width: 900px)
      display: none
    & > *
      position: absolute
    .quarter-circle-blue
      bottom: 0
      left: 15.11375rem
      width: 3.4rem
      height: 3.4rem
      background: #A0DCFF
      border-radius: 100% 0 0 0
    .quarter-circle-green
      bottom: 16.77375rem
      right: 0
      width: 3.4rem
      height: 3.4rem
      background: #C1E5C0
      border-radius: 0 0 0 100%
    .half-circle-pink
      width: 3.4rem
      height: 3.4rem
      border-radius: 100% 0 0 0
      background: #FFC3D8
      bottom: 30.89625rem
      left: 1.7rem
      &::after
        content: ''
        display: block
        position: absolute
        top: 0
        left: 100%
        width: 3.4rem
        height: 3.4rem
        border-radius: 0 100% 0 0
        background: #FFC3D8
    .cat-1
      width: 7.17875rem
      height: 7.17875rem
      bottom: 1.6875rem
      left: 1.6875rem
    .cat-2
      z-index: 2
      width: 9.82375rem
      height: 9.82375rem
      bottom: 21.11875rem
      right: 6.260625rem
    .tomatoes-1
      width: 7.17875rem
      height: 7.17875rem
      bottom: 5.958125rem
      right: 3.99375rem
    .tomatoes-2
      width: 5.29rem
      height: 5.29rem
      bottom: 10.775625rem
      left: 7.509375rem
      z-index: 2
    .lines
      width: 7.084375rem
      height: 7.935rem
      bottom: 8.319375rem
      left: 8.59625rem
      z-index: 1
    .shoes
      width: 5.29rem
      height: 5.29rem
      bottom: 22.205rem
      left: 0
    .dots
      z-index: 1
      bottom: 27.73125rem
      right: 5.1275rem
      div
        display: flex
        margin-top: 0.563125rem
        span
          display: inline-block
          width: 0.18875rem
          height: 0.18875rem
          margin-left: 0.563125rem
          border-radius: 50%
          background: #5d5e62
</style>
