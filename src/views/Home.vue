<template>
  <div class="home">
   
    <UserListe />
  </div>
</template>

<script>
// @ is an alias to /src
import UserListe from '../components/UserListe.vue'
export default {
  name: 'Home',
  components: {
    UserListe,

  }
}
</script>
