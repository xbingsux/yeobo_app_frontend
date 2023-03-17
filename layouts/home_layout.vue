<template>
    <v-app>
      <Nuxt/>
      <v-container>
        <v-bottom-navigation
          fixed
          grow
          app
          mode="shift"
          background-color="#E8ABB5"
          color="#000000"
        >
          <v-btn href="/home">
            <span>Home</span>
            <v-icon>mdi-home</v-icon>
          </v-btn>
  
          <v-btn href="/band">
            <span>K-POP</span>
            <v-icon>mdi-star-circle</v-icon>
          </v-btn>
  
          <v-btn href="/noti">
            <span>Nofitify</span>
            <v-icon>mdi-bell-badge</v-icon>
          </v-btn>
  
          <v-btn href="/profile">
            <span>Profile</span>
            <v-icon>mdi-account-circle</v-icon>
          </v-btn>
        </v-bottom-navigation>
      </v-container>
    </v-app>
</template>
  
<script>
export default {
    middleware: 'auth',
    layout: 'home_layout',
    data () {
        return {
          
        }
    },
}
</script>