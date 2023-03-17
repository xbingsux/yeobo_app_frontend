<template>
  <v-app style="background: #E0BBE4;"> 
    <v-container fill-height fluid>
    
    <div class="max-w-md w-full mx-auto mt-8">
        <v-card class="mx-auto px-6 py-8" max-width="350" width="350">
          <v-row align="center" justify="center">
            <h1 class="text-3xl font-extrabold mb-4 ">Register</h1>
          </v-row>
          <v-form
            ref="form"
            v-model="form"
          >
            <v-text-field
                v-model="username"
                :readonly="loading"
                :rules="[required]"
                class="mb-2"
                clearable
                label="username"
            ></v-text-field>
            <v-text-field
              v-model="email"
              :readonly="loading"
              :rules="emailRules"
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
            <v-text-field
              v-model="password2"
              :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
              :type="show1 ? 'text' : 'password'"
              @click:append="show2 = !show2"
              :readonly="loading"
              :rules="[required,passwordConfirmationRule()]"
              label="Confirm password"
              placeholder="Enter your password"
            ></v-text-field>
    
            <br>
    
            <v-btn
                :loading="loading"
                block
                color="success"
                size="large"
                variant="elevated"
                @click="userRegister()"
            >
              Sign Up
            </v-btn>
            <br><br>
            <v-row align="center" justify="center">
                <h4>Back to  
                  <NuxtLink to="/login">Signin Page </NuxtLink>
                </h4>
              </v-row>
          </v-form>
          
        </v-card>
      
    </div>
  </v-container >
  </v-app> 
</template>

<script>
export default {
    auth: 'guest',
    layout: 'default',
    data() {
        return {
            loading:false,
            show1: false,
            show2: false,
            err: null,
            username:'',
            email: '',
            password: '',
            password2:'',
            emailRules: [ 
                v => /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
            ],
        }
    },
    methods: {
        async userRegister() {
          this.$refs.form.validate()
            console.log("Hello",this.form);
            if(this.form){
                console.log("regis");
                try {
                  this.$axios.setToken(false)
                  await this.$axios.post('auth/local/register', {
                    username: this.username,
                    email: this.email,
                    password: this.password,
                  })
                  this.success = true
                } catch (e) {
                  if (e.response) this.err = e.response.data.error.message
                }
            }
            else{
                console.log("bad");
            }
        },
        required (v) {
            return !!v || 'Field is required'
        },
    },
    computed: {
        passwordConfirmationRule() {
            return () => (this.password === this.password2) || 'Password must match'
        },
    }
}
</script>
<style>
  body {background-color: coral;}
</style>