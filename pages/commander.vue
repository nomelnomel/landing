<template>
  <div class="container">
    <p>
      Merci de remplir le formulaire ci-dessous afin que nous puissions vous
      établir les invitations touristiques pour votre voyage en Russie dans les
      meilleurs délai:
    </p>
    <form action="" class="form">
      <input required type="email" placeholder="Votre adresse E-mail" />
      <input required type="tel" placeholder="Votre numéro de téléphone" />
      <p>Détails de voyage:</p>
      <input required type="text" placeholder="Date d’arrivée" />
      <input required type="text" placeholder="Date de départ" />
      <input required type="text" placeholder="Villes et logement" />

      <SmallForm
        v-for="(voyageur, i) in voyageurs"
        :key="voyageur.numero"
        :number="i"
        :voyageur="voyageur"
      />
      <button class="btn" @click.prevent="addVoyageur">Add voyageur</button>
      <button type="submit">send form</button>
    </form>
  </div>
</template>

<script>
import SmallForm from '@/components/SmallForm'

export default {
  name: 'Commander',
  components: {
    SmallForm,
  },
  data() {
    return {
      voyageurs: [],
    }
  },
  methods: {
    addVoyageur() {
      const newV = {
        nom: '',
        prenom: '',
        nation: '',
        sex: '',
        date: '',
        numero: '',
      }
      this.voyageurs.push(newV)
    },
  },
}
</script>

<style scoped lang="scss">
.form {
  display: flex;
  flex-direction: column;

  input {
    height: 30px;
    max-width: 400px;
    margin-bottom: 20px;
  }
}
</style>
