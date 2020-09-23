<template>
  <v-app>
    <v-main>
      <UserComp></UserComp>
    </v-main>
  </v-app>
</template>

<script>
import UserComp from './components/User.vue'

export default {
  name: 'App',
  components: {
    UserComp
  },
  data: () => ({
    //
  }),
};
</script>
