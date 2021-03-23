<template lang="pug">
  header.header
    .header__content
      h1.ttl Найдется все
      p Самые важные вещи для качественной жизни. Ласковые коты, вкусные&nbsp;
        | помидоры и умопомрачительные носки!
      category-picker
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
  &__content
    max-width: 976px
    margin: 0 auto
    h1
      font-style: normal
      font-weight: 800
      font-size: 4.5rem
      line-height: 126%
      font-feature-settings: 'liga' off
    p
      margin: 3.125rem 0
      font-size: 1.125rem
      line-height: 178%
      font-feature-settings: 'liga' off
</style>
