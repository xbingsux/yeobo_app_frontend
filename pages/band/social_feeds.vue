<template>
   
    <v-app style="background-color: #CCCCFF;"> 
        
        <v-system-bar
            height="30"
        ></v-system-bar>
        <v-app-bar
            fixed
            color="#E8ABB5"
            height="60"
        >
            <v-app-bar-title>{{kpop_name}}</v-app-bar-title>
        </v-app-bar>
       <div class="d-flex justify-center">
            <v-overlay
                v-model="overlay"
            >
                <v-progress-circular
                    :size="100"
                    :width="7"
                    color="#E8ABB5"
                    indeterminate
                ></v-progress-circular>
            </v-overlay>
        </div>
        <v-card height="0" style="margin-top: 40px"></v-card>
        <div v-for="item in feeds_items" :key="item.post_id">
        <v-card
            height=auto
            color="#26c6da"
            style="margin: 0px 10px 10px 10px;"
            @click="LinkSocial(item)"
        >
            
            <v-card-actions>
                <v-list-item class="grow">
                    <!-- <v-list-item-avatar color="grey darken-3">
                        <v-img
                            class="elevation-6"
                            alt=""
                            src="https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BIGBANG_3.png?alt=media&token=eccc4cec-e340-4680-93fc-80b4981eea20"
                        ></v-img>
                    </v-list-item-avatar> -->
          
                    <v-list-item-content>
                        <v-list-item-title>{{item.source_name}}</v-list-item-title>
                    </v-list-item-content>
        
                    <v-row align="center" justify="end" >
                        <span class="subheading">{{item.source_type}}</span>
                        <v-icon class="mr-1">
                            mdi-twitter
                        </v-icon>
                    </v-row>
                </v-list-item>
            </v-card-actions>
            <div v-if="item.post_media_items.length > 0">
                <div v-if="item.post_media_items[0].media_type == 'photo'">
                    <v-card-item>
                        <v-img
                            cover
                            height="250"
                            :src=item.post_media_items[0].media_url
                        ></v-img>
                    </v-card-item>
                </div>
                
            </div>
            <v-card-text>
                {{item.post_original}}
            </v-card-text>
            <v-card-text>
                {{item.datetime_original}} - {{item.datetime_relative}} ago
            </v-card-text>
        </v-card>
        </div>
        <!-- <v-card
            height=auto
            color="#26c6da"
            style="margin: 0px 10px 10px 10px;"
        >
            <v-card-actions>
                <v-list-item class="grow">
                    <v-list-item-avatar color="grey darken-3">
                        <v-img
                            class="elevation-6"
                            alt=""
                            src="https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BTS_1.png?alt=media&token=49e37551-3960-4924-8e6e-4494e349c461"
                        ></v-img>
                    </v-list-item-avatar>
          
                    <v-list-item-content>
                        <v-list-item-title>BTS</v-list-item-title>
                    </v-list-item-content>
        
                    <v-row align="center" justify="end" >
                        <span class="subheading">Twitter</span>
                        <v-icon class="mr-1">
                            mdi-twitter
                        </v-icon>
                    </v-row>
                </v-list-item>
            </v-card-actions>
            <v-card-text class="text-h5 font-weight-bold">
                "Turns out semicolon-less style is easier and safer in TS because most gotcha edge cases are type invalid as well."
            </v-card-text>
        </v-card> -->
        <v-card height="0" style="margin-top: 20px"></v-card>
    </v-app>
</template>

<script>
import { Z_UNKNOWN } from 'zlib'

    export default {
        middleware: 'auth',
        layout: 'home_layout',
        data () {
            return {
                overlay:false,
                kpop_name: "Name",
                kpop_id: null,
                feeds_items: [],
            }
        },
        methods: {
            async GetSocialFeed() {
                this.overlay=true
                this.kpop_id = this.$router.currentRoute.query['id']
                console.log("param : ",this.kpop_id);
                await this.$axios
                .get("http://13.212.53.96:5002/api/v1.0/kpop/social_feeds?kpop_name="+this.kpop_id+"&sources_list=[%22Twitter%22]")
                    .then(res=>{
                        this.kpop_name = res.data.response.kpop_name
                        // this.feeds_items = res.data.response.feeds_data?res.data.response.feeds_data:null;
                        let raw = res.data.response.feeds_data?res.data.response.feeds_data:null;
                        let item = []
                        for (let index = 0; index < 30; index++) {
                            item.push(raw[index])
                        }
                        this.feeds_items = item
                        console.log("res : ",this.feeds_items);
                    })
                    .catch(err=>{
                        console.log("err : ",err);
                    })
                this.overlay=false
            },
            LinkSocial(item){
                console.log("item",item);
                window.location.href = item.url_link;
            }
        },
        created(){
            this.GetSocialFeed()
        }
    }
</script>