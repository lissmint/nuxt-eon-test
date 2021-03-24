<template lang="pug">
  transition(name="fade")
    .sock
      .sock__outer
        .sock__inner
          .sock__img-container()
            transition-group(name="fade")
              img(
                v-for="(img, i) in sock.images"
                :key="i"
                :src="img"
                alt="sock.name"
                v-show="i === activeSock"
              )
            .sock__img-container--controls
              span(
                v-for="(i) in sock.images.length"
                :key="i"
                :class="{active: i - 1 === activeSock }"
                @mouseenter.stop="activeSock = i - 1"
                @click.stop="activeSock = i - 1"
              )
          h2 {{ sock.name }}
</template>

<script>
export default {
  name: 'SockCard',
  props: {
    sock: {
      type: Object,
      default: () => {},
      required: true,
    },
  },
  data: () => ({
    activeSock: 0,
  }),
}
</script>

<style lang="sass" scoped>
.sock
  width: calc(100% / 2 - 1.5625rem)
  margin-bottom: 3.125rem
  position: relative
  box-shadow: 0px 0px 1px rgba(12, 26, 75, 0.24), 0px 3px 8px -1px rgba(50, 50, 71, 0.05)
  &:not(:nth-child(even))
    margin-right: 3.125rem
  &__outer
    position: relative
    padding-top: 368 / 470 * 100%
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
  &__img-container
    //height: 60%
    flex-grow: 1
    margin-bottom: 1.5625rem
    position: relative
    img
      position: absolute
      top: 0
      left: 0
      width: 100%
      height: 100%
      object-fit: cover
    &--controls
      position: absolute
      bottom: 1rem
      left: 0
      text-align: center
      transform: translateY(-50%)
      width: 100%
      span
        width: 1.25rem
        height: .625rem
        display: inline-block
        cursor: pointer
        background: white
        opacity: .5
        &.active
          opacity: 1
        &:not(:last-child)
          margin-right: .625rem
  @media screen and (max-width: 900px)
    h2
      font-size: 1.2rem
    &__outer
      padding-top: 140%
  @media screen and (max-width: 900px)
    width: 100%
    &:not(:nth-child(even))
      margin-right: 0
    &__outer
      padding-top: 70%
  @media screen and (max-width: 500px)
    &__outer
      padding-top: 110%
</style>
