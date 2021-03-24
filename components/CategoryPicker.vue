<template lang="pug">
  .categories
    label.categories__option(
      v-for="option in options"
      :class="{active: option.value === picked}"
    ) {{ option.name }}
      input(
        v-model="picked"
        type="radio"
        :value="option.value"
      )
</template>

<script>
export default {
  name: 'CategorySelect',
  data: () => ({
    picked: '',
    options: [
      {
        name: 'Помидоры',
        value: 'tomatoes',
      },
      {
        name: 'Коты',
        value: 'cats',
      },
      {
        name: 'Носки',
        value: 'socks',
      },
    ],
  }),
  watch: {
    picked(val) {
      this.$emit('categoryPicked', this.picked)
    },
  },
}
</script>

<style lang="sass" scoped>
.categories
  display: flex
  &__option
    cursor: pointer
    flex: 1
    padding: 1.1875rem .2rem
    border-radius: 2.0625rem
    text-align: center
    margin-right: 1.25rem
    line-height: 1.375rem
    //background: linear-gradient(44.11deg, #CD10FF 15.75%, #9F06FF 84.63%)
    background: linear-gradient(44.11deg, #10C6FF 15.75%, #9F06FF 84.63%) top right
    background-size: 300%
    transition: .5s ease-out
    &.active,
    &:hover
      background-size: 100%
    input
      display: none
  @media screen and (max-width: 450px)
    flex-direction: column
    flex-wrap: wrap
    &__option
      width: 100%
      padding: .7rem .2rem
      &:not(:last-child)
        margin: 0 0 1rem
</style>
