<template>
    <v-app style="background-color: #CCCCFF;">
        <v-app-bar
            fixed
            color="#E8ABB5"
            height="60"
        >
            <v-app-bar-title>K-POP</v-app-bar-title>
        </v-app-bar>
        <v-container>
            <v-card height="0" style="margin-top: 60px"></v-card>
            <v-row dense  align="center" justify="center">
                <v-col
                    v-for="card in cards"
                    :key="card.title"
                    :cols="card.flex"
                >
                    <v-card
                        height="170"
                        width="170"
                        color="white"
                        style="margin: 5px 0px 5px 0px; border-radius:20px;"
                        @click="GoSocialFeed(card)"
                    >
                        <v-img
                            :src= card.src
                            height=80%
                            class="grey darken-4"
                        >
                            
                        </v-img>
                        <v-row align="center" justify="center" style="margin: auto">
                            <h2 style="font-weight: 1200;-webkit-text-stroke: 1px yellow;">{{card.title}}</h2>
                        </v-row>
                    </v-card>
                </v-col>
                
                <!-- <v-card
                    height="170"
                    width="170"
                    color="white"
                    style="margin: 5px 10px 5px 10px;"
                >
                </v-card>
                <v-card
                    height="170"
                    width="170"
                    color="white"
                    style="margin: 5px 10px 5px 10px;"
                >
                </v-card> -->
            </v-row>
            <v-card height="0" style="margin-top: 30px"></v-card>
        </v-container>
    </v-app>
</template>

<script>
    export default {
        middleware: 'auth',
        layout: 'home_layout',
        data () {
            return {
                cards:  [
                            { id:"BTS",title: 'BTS', src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BTS_3.png?alt=media&token=12c7917f-6388-4ffa-8d78-a4faa35209d0', flex: 6 },
                            { id:"BLACKPINK",title: 'BLACKPINK', src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BLACKPINK_1.png?alt=media&token=4faa7b78-c300-497f-be9f-dac62b690449', flex: 6 },
                            { id:"TWICE",title: 'TWICE', src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/TWITCH_1.png?alt=media&token=06da8d8b-1911-4481-8cd9-bf2024db704f', flex: 6 },
                            { id:"G-DRAGON",title: 'BIGBANG', src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BIGBANG_3.png?alt=media&token=eccc4cec-e340-4680-93fc-80b4981eea20', flex: 6 },
                            { id:"EXO",title: 'EXO', src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/EXO_4.png?alt=media&token=9a02c5b5-dc2e-4ae0-ac4c-17c360fdcb1a', flex: 6 },
                            { id:"Seventeen",title: 'Seventeen', src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/Seventeen_2.png?alt=media&token=4b62b852-6d1c-4656-8173-e5d71964272e', flex: 6 },
                            { id:"NTC+Dream",title: 'NTC Dream', src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/NTC_Dream_1.png?alt=media&token=1aa19b89-4556-488a-9940-6a976b5e79cb', flex: 6 },
                            { id:"Treasure",title: 'Treasure', src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/treasure-tn.jpg?alt=media&token=1c95b306-245b-4a36-90a3-a4678fa12c51', flex: 6 },
                        ],
            }
        },
        methods: {
            async GoSocialFeed(card) {
                // console.log("Hello",card.id)
                window.location.href = "/band/social_feeds?id="+card.id;

            }
        },
    }
</script>