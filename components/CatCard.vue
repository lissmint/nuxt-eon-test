<template lang="pug">
  transition(name="fade")
    .cat
      .cat__outer
        .cat__inner
          .cat__img
            img(:src="cat.image" alt="cat.name")
          .cat__info
            h2 {{cat.name}}
            ul
              li(
                v-for="perk in cat.advantages.slice(0,3)"
                :key="perk"
              ) — {{perk}}
</template>

<script>
export default {
  name: 'CatCard',
  props: {
    cat: {
      type: Object,
      default: () => {},
      required: true,
    },
  },
}
</script>

<style lang="sass" scoped>
.cat
  width: calc(100% / 2 - 1.5625rem)
  margin-bottom: 3.125rem
  position: relative
  box-shadow: 0px 0px 1px rgba(12, 26, 75, 0.24), 0px 3px 8px -1px rgba(50, 50, 71, 0.05)
  &:not(:nth-child(even))
    margin-right: 3.125rem
  &__outer
    position: relative
    //top: 0
    //left: 0
    padding-top: 461 / 470 * 100%
    height: 0
    width: 100%
    background: white
    overflow: hidden
  &__inner
    position: absolute
    top: 0
    left: 0
    width: 100%
    height: 100%
    padding: 1.5625rem
    display: flex
    flex-direction: column
  &__img
    height: 60%
    margin-bottom: 1.5625rem
    img
      width: 100%
      height: 100%
      object-fit: cover
  &__info
    ul
      margin-top: 1.25rem
      list-style: none
      padding: 0
      color: #425466
  @media screen and (max-width: 900px)
    h2
      font-size: 1.2rem
    ul
      margin-top: .5rem
  @media screen and (max-width: 768px)
    width: 100%
    &:not(:nth-child(even))
      margin-right: 0
  @media screen and (max-width: 768px)
    &__img
      height: 40%
</style>
