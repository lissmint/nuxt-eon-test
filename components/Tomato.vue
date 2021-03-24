<template lang="pug">
  .tomato
    .tomato__img
      loader(v-show="!imgLoaded")
      transition(name="fade")
        img(
          v-show="imgLoaded"
          :src="tomato.image"
          alt="tomato"
          @load="imgLoaded = true"
        )
    .tomato__info
      h2 {{ tomato.name }}
      p {{ tomato.description }}
      h3 {{ tomato.price }} руб.
</template>

<script>
import Loader from '~/components/Loader'
export default {
  name: 'TomatoCard',
  components: { Loader },
  props: {
    tomato: {
      type: Object,
      default: () => {},
      required: true,
    },
  },
  data: () => ({
    imgLoaded: false,
  }),
}
</script>

<style lang="sass" scoped>
.tomato
  width: 100%
  margin-bottom: 3.125rem
  padding: 1.5625rem
  display: flex
  box-shadow: 0px 0px 1px rgba(12, 26, 75, 0.24), 0 3px 8px -1px rgba(50, 50, 71, 0.05)
  &__img
    min-width: 21.875rem
    height: 15.625rem
    position: relative
    flex: 1
    & > *
      position: absolute
      top: 0
      left: 0
      width: 100%
      height: 100%
      object-fit: cover
  &__info
    width: 65%
    color: #425466
    padding-left: 3.125rem
    p
      font-size: 1.125rem
      line-height: 133%
      margin: 1.25rem 0
  @media screen and (max-width: 768px)
    flex-direction: column
    &__img
      flex: none
      width: 100%
    &__info
      width: 100%
      padding-left: 0
</style>
