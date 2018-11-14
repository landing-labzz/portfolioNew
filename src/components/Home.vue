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
    <section id="about" class="pt-5 pb-5">
      <Title
        titleLg="Обо мне"
        description="Не много информации о себе"
       />
       <About />

        <main class="" style="padding-top: 100px;">
          <Title
            titleLg="Навыки"
            description="Коротко о навыках"
           />
          <Skills/>

        </main>
    </section>
    <section id="portfolio" class="pt-5 pb-5">
      <Title
        titleLg="Портфолио"
        description="Я старался сделать что то новое, поэтому вы можете оценить портфолио, и написать отзыв."
       />
       <Portfolio />
    </section>
    <Features />
    <Social />
    <Footer />
  </main>
</template>

<script>
import Header from './Header'
import Title from './Title'
import Work from './Work'
import Portfolio from './Portfolio'
import Features from './Features'
import Social from './Social'
import Footer from './Footer'
import Testimonials from './Testimonials'
import About from './About'
import Skills from './Skills'
export default {
  name: 'home',
  components: {
    Header,
    Title,
    Work,
    Portfolio,
    Features,
    Social,
    Footer,
    Testimonials,
    About,
    Skills,
  },
}
</script>

<style lang="css">
</style>
