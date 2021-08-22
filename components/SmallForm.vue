<template>
  <div class="form">
    <p>Voyageur {{ number + 1 }}</p>
    <input
      v-model="person.nom"
      required
      type="text"
      placeholder="Nom (comme dans le passeport)"
    />
    <input
      v-model="person.prenom"
      required
      type="text"
      placeholder="Prénom (comme dans le passeport)"
    />
    <input
      v-model="person.nation"
      required
      type="text"
      placeholder="Nationalité"
    />
    <input v-model="person.sex" required type="text" placeholder="Sexe" />
    <input
      v-model="person.date"
      required
      type="text"
      placeholder="Date de naissance"
    />
    <input
      v-model="person.numero"
      required
      type="text"
      placeholder="Numéro de passeport"
    />
  </div>
</template>

<script>
export default {
  name: 'SmallForm',
  props: {
    number: {
      type: Number,
      default: 0,
    },
    voyageur: {
      type: Object,
      default: () => ({}),
    },
  },
  data() {
    return {
      person: { ...this.voyageur },
    }
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
