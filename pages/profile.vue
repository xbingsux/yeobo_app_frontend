<template>
    <v-app style="background-color: #CCCCFF;">
        <v-container>
            <v-col align="center">
                <h1>Profile</h1>
            </v-col>
            <v-col align="center" >
                    <v-avatar size="150" style="margin-bottom: 30px;">
                        <img
                            src="https://cdn.vuetifyjs.com/images/john.jpg"
                            alt="John"
                        >
                    </v-avatar>
            </v-col>
            <v-row >
                    <!-- <v-text-field
                        label="USER"
                        value="Hello"
                        filled
                        outlined
                        rounded
                        dense
                        readonly
                        append-outer-icon="mdi-account-edit"
                    ></v-text-field> -->
                    <!-- <v-col 
                        align="center"
                        justify="center"
                    >
                        <v-btn
                            class="ma-4"
                            :loading="loading"
                            :disabled="loading"
                            color="white"
                            large
                        >
                            <div class="ma-16">My name : xBINGSUx</div>
                            <v-icon>
                                mdi-pencil
                            </v-icon>
                        </v-btn>
                        <v-btn
                            class="ma-4"
                            :loading="loading"
                            :disabled="loading"
                            color="white"
                            large
                        >
                            <div class="ma-16">My email : xBINGSUx</div>
                            <v-icon>
                                mdi-pencil
                            </v-icon>
                        </v-btn>
                        <v-btn
                            class="ma-4"
                            :loading="loading"
                            :disabled="loading"
                            color="white"
                            large
                        >
                            <div class="ma-16">Email Verify : xBINGSUx</div>
                            <v-icon>
                                mdi-pencil
                            </v-icon>
                        </v-btn>
                        <v-btn
                            class="ma-4"
                            :loading="loading"
                            :disabled="loading"
                            color="white"
                            large
                        >
                            <div class="ma-16">Email Verify : xBINGSUx</div>
                            <v-icon>
                                mdi-pencil
                            </v-icon>
                        </v-btn>
                    </v-col> -->
                    
                    
                
            </v-row>
            <v-row align="center" justify="center" style="margin: 20px;">
                <v-card width="350" max-width="350" color="white" style="border-radius:20px;">
                    <v-card-actions>
                        <v-toolbar-title style="margin-right: 20px; color:gray">
                            username :
                        </v-toolbar-title>
                        <v-toolbar-title>
                            {{loggedInUser.username}}
                        </v-toolbar-title>
                        <v-spacer></v-spacer>
                        <v-btn icon>
                            <v-icon>mdi-pencil</v-icon>
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-row>
            <v-row align="center" justify="center" style="margin: 20px;">
                <v-card width="350" max-width="350" color="white" style="border-radius:20px;">
                    <v-card-actions>
                        <v-toolbar-title style="margin-right: 20px; color:gray">
                            email :
                        </v-toolbar-title>
                        <v-toolbar-title>
                            {{loggedInUser.email}}
                        </v-toolbar-title>
                        <v-spacer></v-spacer>
                        <v-btn icon>
                            <v-icon>mdi-pencil</v-icon>
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-row>
            <v-row align="center" justify="center" style="margin: 20px;">
                <v-card width="350" max-width="350" color="white" style="border-radius:20px;">
                    <v-card-actions>
                        <v-toolbar-title style="margin-right: 20px; color:gray">
                            confirmed :
                        </v-toolbar-title>
                        <v-toolbar-title>
                            {{loggedInUser.confirmed}}
                        </v-toolbar-title>
                        <v-spacer></v-spacer>
                        <v-btn icon>
                            <v-icon>mdi-pencil</v-icon>
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-row>
            <v-row align="center" justify="center" style="margin: 20px;">
                <v-card width="350" max-width="350" color="white" style="border-radius:20px;">
                    <v-card-actions>
                        <v-toolbar-title style="margin-right: 20px; color:gray">
                            change password
                        </v-toolbar-title>
                        <v-spacer></v-spacer>
                        <v-btn icon>
                            <v-icon>mdi-pencil</v-icon>
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-row>
            <v-row align="center" justify="center" style="margin-top: 20px; margin-bottom: 20px;">
                <v-btn
                    rounded
                    color="red"
                    dark
                    @click="userLogout()"
                    >
                    Logout
                </v-btn>
            </v-row>
        </v-container>
    </v-app>
</template>
<script>
    import { mapGetters } from 'vuex'
    export default {
        middleware: 'auth',
        layout: 'home_layout',
        data () {
            return {
            }
        },
        methods: {
            async userLogout() {
                await this.$auth.logout()
            },
        },
        computed: {
            ...mapGetters(['loggedInUser']),
        },
    }
</script>