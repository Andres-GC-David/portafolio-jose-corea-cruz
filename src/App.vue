<template>
  <div>
    <Hero />
    <About />
    <Experience />
    <Projects />
    <Education />
    <Contact />
    <Footer />
  </div>
</template>

<script>
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Experience from './components/Experience.vue'
import Education from './components/Education.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue';
import Projects from './components/Projects.vue';


export default {
  components: { Hero, About, Education, Contact, Footer, Projects, Experience },
}
</script>
