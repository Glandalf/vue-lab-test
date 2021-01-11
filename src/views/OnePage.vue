<template>
    <div>
        <Accueil id="accueil"/>
        <Apropos id="about"/>
        <Galerie id="galerie"/>
        <Contact id="contact"/>
    </div>
</template>

<script>
import Accueil from '../components/Accueil'
import Apropos from '../components/About'
import Contact from '../components/contact'
import Galerie from '../components/galerie'

export default {
  components: { Accueil, Apropos, Contact, Galerie }
}
</script>
