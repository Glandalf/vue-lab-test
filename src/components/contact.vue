<template>
    <section id="contact">
        <h2>contact</h2>
        <ul class="actions">
          <li><button :class="!professionnel? 'active': 'inactive'" @click="professionnel = false">Particuliers</button></li>
          <li><button :class="professionnel? 'active': 'inactive'" @click="professionnel = true">Professionnel</button></li>
        </ul>
          <input type="radio" name="option1" value="1">a<br/>
          <input type="radio" name="option1" value="2">b<br/>
          <input type="radio" name="option1" value="3">c<br/>
        <hr>
          <input type="radio" name="option2" value="1aaaaa">aaaaaa<br/>
          <input type="radio" name="option2" value="2aaaaa">baaaaa<br/>
          <input type="radio" name="option2" value="3aaaaa">caaaaa<br/>

          <input type="checkbox" checked> a
          <input type="checkbox"> b
          <input type="checkbox"> ba
          <input type="checkbox"> badzfd
          <input type="checkbox"> c²
        <form v-if="!professionnel && !mailEnvoye" method="post" action="#" @submit.prevent="envoiFormulaire">
          <h3>Vous êtes un particulier !</h3>
            <label for="name">Name </label>
            <input type="text" name="name" id="name" />

            <label for="name">Prenom </label>
            <input type="text" name="prenom" id="prenom" />

            <label for="name">Telephone </label>
            <input type="tel" name="tel" id="tel" />

            <label for="name">Email </label>
            <input type="email" name="mail" id="mail" />

            <ul class="actions">
              <li><button>Envoyer</button></li>
              <li><button>Réinitialiser</button></li>
            </ul>
        </form>
        <form v-else-if="professionnel && !mailEnvoye" method="post" action="#" @submit.prevent="envoiFormulaire">
            <h3>Vous êtes une entreprise !</h3>
            <label for="name">Dénomination sociale</label>
            <input type="text" name="name" id="name" />

            <label for="name">Telephone</label>
            <input type="tel" name="tel" id="tel" />

            <label for="name">Email</label>
            <input type="email" name="mail" id="mail" />

            <ul class="actions">
              <li><button>Envoyer</button></li>
              <li><button>Réinitialiser</button></li>
            </ul>
        </form>
        <span v-else>Nous avons bien reçu votre message et vous contacterons dans les prochains jours. Bisoubisou</span>
    </section>
</template>

<script>
export default {
  data: () => {
    return {
      mailEnvoye: false,
      professionnel: false
    }
  },
  methods: {
    envoiFormulaire () {
      console.log('envoi du form')
      // alert('coincoin')
      fetch('https://api.asciiparait.fr/contact.php')
        .then(response => response.json())
        .then(data => {
          // Afficher que l'on a bien envoyé le message
        })
      this.mailEnvoye = true
    }
  }
}
</script>

<style scoped>
    * {
        text-align: left;
    }
    label {
        display: block;
        width: calc(100% - 42px);
    }
    ul.actions {
      display: flex;
    }
    ul.actions li {
      list-style-type: none;
    }
    ul.actions li > button {
      border: 0;
      padding: 10px 20px;
      font-weight: bold;
      background: #ddd;
    }
    ul.actions li > button.active {
      color: #fff;
      background: rgb(42, 57, 141);
    }
    ul.actions li > button.inactive {
      color: #888;
      background: rgb(238, 238, 238);
    }
    ul.actions li > button:hover {
      cursor: pointer;
      background: #eee;
    }
    ul.actions li:first-child > button {
      border-radius: 8px 0 0 8px;
    }
    ul.actions li:last-child > button {
      border-radius: 0 8px 8px 0;
    }
</style>
