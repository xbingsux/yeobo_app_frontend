// frontend/pages/user/Login.vue
<template>
  <v-app style="background: #E0BBE4;"> 
    <v-container fill-height fluid>
    <div class="max-w-md w-full mx-auto mt-8">
    
        
        <v-card class="mx-auto px-6 py-8" max-width="350" width="350">
          <v-row align="center" justify="center">
            <h1 class="text-3xl font-extrabold mb-4 ">Sign in</h1>
          </v-row>
          <v-form
            v-model="form"
            @submit.prevent="userLogin"
          >
            <v-text-field
              v-model="email"
              :readonly="loading"
              :rules="[required]"
              class="mb-2"
              clearable
              label="Email"
            ></v-text-field>
            <v-text-field
              v-model="password"
              :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
              :type="show1 ? 'text' : 'password'"
              @click:append="show1 = !show1"
              :readonly="loading"
              :rules="[required]"
              label="Password"
              placeholder="Enter your password"
            ></v-text-field>
    
            <br>
    
            <v-btn
              :disabled="!form"
              :loading="loading"
              block
              color="success"
              size="large"
              type="submit"
              variant="elevated"
            >
              Sign In
            </v-btn>
            <br><br>
            <v-row align="center" justify="center">
              <h4>Not a menber? 
                <NuxtLink to="/register">Signup now </NuxtLink>
              </h4>
            </v-row>
            
          </v-form>
          
        </v-card>
      
    </div>
  </v-container>
  </v-app> 
</template>

<script>
export default {
  auth: 'guest',
  layout: 'default',
  data() {
    return {
      show1: false,
      err: null,
      email: '',
      password: '',
    }
  },
  methods: {
    async userLogin() {
      console.log("Login Hello",this.email);
      console.log("Login Hello",this.password);
      try {
        await this.$auth.loginWith('local', {
          data: { identifier: this.email, password: this.password },
        })
        console.log("Try");
      } catch (e) {
        if (e.response) this.err = e.response.data.error.message
        console.log("catch");
      }
    },
    required (v) {
        return !!v || 'Field is required'
    },
  },
}
</script>
<style>
  body {background-color: coral;}
</style>