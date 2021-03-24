<template lang="pug">
 .container
   app-header(@categoryPicked="handleCategoryPick")
   transition(name="fade")
     .content(v-if="!loading")
       .content__container(v-if="pickedCategory === 'tomatoes'")
            tomato-card(
              v-for="tomato in categoryItems"
              :key="tomato.name"
              :tomato="tomato"
            )
       .content__container(v-if="pickedCategory === 'cats'")
           cat-card(
             v-for="cat in categoryItems"
             :key="cat.name"
             :cat="cat"
           )
       .content__container(v-if="pickedCategory === 'socks'")
           sock-card(
             v-for="sock in categoryItems"
             :key="sock.name"
             :sock="sock"
           )
</template>

<script>
import AppHeader from '~/components/AppHeader'
import TomatoCard from '~/components/Tomato'
import CatCard from '~/components/CatCard'
export default {
  components: { CatCard, TomatoCard, AppHeader },
  data: () => ({
    pickedCategory: '',
    categoryItems: [],
    loading: false,
  }),
  watch: {
    loading(val) {
      if (!val) {
        console.log('bonk')
        const headerHeight = document.querySelector('header').offsetHeight
        window.scrollTo(0, headerHeight)
      }
    },
  },
  methods: {
    async handleCategoryPick(category) {
      this.loading = true
      this.pickedCategory = category
      try {
        const resp = await this.$axios.get('/api' + category, {
          mode: 'no-cors',
        })
        this.categoryItems = resp.data
        this.loading = false
      } catch (e) {
        this.loading = false
        console.log(e)
      }
    },
  },
}
</script>

<style lang="sass">
html
  font-size: 16px
body
  scroll-behavior: smooth
  font-size: 1.125rem
  @media screen and (min-width: 1920px)
    font-size: 0.94vw
.content
  margin: 0 auto
  max-width: 75rem
  min-width: 320px
  &__container
    width: 83%
    padding-top: 4.375rem
    display: flex
    flex-wrap: wrap
    @media screen and (max-width: 1200px)
      width: 100%
      padding: 4.375rem 1rem 1rem
.fade-enter-active, .fade-leave-active
  transition: opacity .5s
.fade-enter, .fade-leave-to
  opacity: 0
h2
  font-weight: 600
  font-size: 1.5rem
  color: #425466
</style>
