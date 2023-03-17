<template>
    <v-app style="background-color: #CCCCFF;">
        <v-container>
        <v-system-bar
            height="30"
        ></v-system-bar>
        <v-app-bar
            flat="true"
            fixed
            color="#E8ABB5"
            height="60"
        >
            <v-app-bar-title>Notification</v-app-bar-title>
        </v-app-bar>
        <div style="height: 20px;"></div>
        
        <div v-for="item in notification" :key="item.id">
            <v-card
                height="80"
                color="white"
                style="margin: 20px 10px 20px 10px;"
            >
                <div class="row" style="padding: 10px 10px 10px 20px ;">
                    <v-avatar 
                            color="red"
                            size="60"
                        >
                            <v-img
                                :src=item.src
                            ></v-img>
                    </v-avatar>
                    <div style="margin: 0px 10px 10px 20px;">
                        <h3>{{item.title}}</h3>
                        <div class="caption display: block" style="width: 250px; height: 40px;">{{item.text}}</div>
                    </div>
                </div>
            </v-card>
        </div>
    </v-container>
    </v-app>
</template>

<script>
    export default {
        middleware: 'auth',
        layout: 'home_layout',
        data () {
            return {
                notification :[
                    {
                        src:"https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BIGBANG_3.png?alt=media&token=eccc4cec-e340-4680-93fc-80b4981eea20",
                        title:"BIGBANG",
                        text:"text ever since the 1500s, when an unknown printer took a galley of type and ..."
                    },
                    {
                        src:"https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BTS_1.png?alt=media&token=49e37551-3960-4924-8e6e-4494e349c461",
                        title:"BTS",
                        text:"ribution of letters, as opposed to using 'Content here, content here', making ... "
                    },
                    {
                        src:"https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/EXO_1.png?alt=media&token=d18dfbb0-d9cf-4c10-9f76-6723d4061b96",
                        title:"EXO",
                        text:"ned chunks as necessary, making this the first true generator on the Internet ..."
                    },
                    {
                        src:"https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BIGBANG_3.png?alt=media&token=eccc4cec-e340-4680-93fc-80b4981eea20",
                        title:"BIGBANG",
                        text:"text ever since the 1500s, when an unknown printer took a galley of type and ..."
                    },
                    {
                        src:"https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BTS_1.png?alt=media&token=49e37551-3960-4924-8e6e-4494e349c461",
                        title:"BTS",
                        text:"ribution of letters, as opposed to using 'Content here, content here', making ... "
                    },
                    {
                        src:"https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/EXO_1.png?alt=media&token=d18dfbb0-d9cf-4c10-9f76-6723d4061b96",
                        title:"EXO",
                        text:"ned chunks as necessary, making this the first true generator on the Internet ..."
                    },
                ]
            }
        },
    }
</script>