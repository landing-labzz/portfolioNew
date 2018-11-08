<template lang="html">
  <main>
    <Header />
    <section id="work" class="pt-5 pb-5 pl-3 pr-3">
      <Title
        titleLg="Процесс разработки"
        description="Стремление помочь, превыше всего. Вы можете задать интересующий вас вопрос или предложить вариант улучшения работы."
       />
       <Work />
    </section>
    <section id="portfolio" class="pt-5 pb-5">
      <Title
        titleLg="Портфолио"
        description="Я старался сделать что то новое, поэтому вы можете оценить портфолио, и написать отзыв."
       />
       <Portfolio />
    </section>
  </main>
</template>

<script>
import Header from './Header'
import Title from './Title'
import Work from './Work'
import Portfolio from './Portfolio'
export default {
  name: 'home',
  components: {
    Header,
    Title,
    Work,
    Portfolio,
  },
}
</script>

<style lang="css">
</style>
