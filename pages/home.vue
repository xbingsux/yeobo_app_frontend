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
            height="45"
        >
            <v-app-bar-title>Home2</v-app-bar-title>
        </v-app-bar>

        <v-card
            height="200"
            color="white"
            style="margin: 20px 10px 30px 10px;"
        >
                
                    <v-carousel 
                        :show-arrows="false"
                        cycle="true"
                        interval="6000"
                        height="200"
                        hide-delimiters
                    >
                        <v-carousel-item
                        v-for="(item,i) in items"
                        :key="i"
                        :src="item.src"
                        ></v-carousel-item>
                    </v-carousel>
        </v-card>
        <div align="start" style="margin: 0px 0px 0px 20px">
            <h1>Popular Tags</h1>
        </div>
        <v-row style="padding: auto;">
            <v-col>
                <v-chip-group
                    active-class="primary--text"
                    column
                    style="margin: 10px 10px 10px 10px;"
                >
                    <v-chip
                        v-for="tag in tags"
                        :key="tag"
                    >
                        {{ tag }}
                    </v-chip>
                </v-chip-group>
            </v-col>
        </v-row> 
        <!-- <v-card
            height="300"
            color="white"
            style="margin: 0px 10px 10px 10px;"
        >
        
        </v-card> -->
       
        <v-card
            height=auto
            color="#9FE2BF"
            style="margin: 0px 10px 10px 10px;"
        >
            <v-card-item>
                <v-img
                    cover
                    height="200"
                    src="https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BTS_4.png?alt=media&token=05b86144-1dd9-48e2-bfcb-afa49f07d5fb"
                ></v-img>
            </v-card-item>
            <!-- <v-card-text class="text font-weight-bold">
                "Turns out semicolon-less style is easier and safer in TS because most gotcha edge cases are type invalid as well."
            </v-card-text>  -->
            <v-card-actions>
                <v-list-item class="grow">
                    <v-list-item-avatar color="grey darken-3">
                        <v-img
                            class="elevation-6"
                            alt=""
                            src="https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BIGBANG_3.png?alt=media&token=eccc4cec-e340-4680-93fc-80b4981eea20"
                        ></v-img>
                    </v-list-item-avatar>
          
                    <v-list-item-content>
                        <v-list-item-title>Bigbang</v-list-item-title>
                    </v-list-item-content>
        
                    <v-row align="center" justify="end" >
                        <!-- <span class="subheading">Twitter</span> -->
                        
                        <v-btn icon href="/band/calendar">
                            <v-icon large>
                                mdi-calendar-multiselect-outline
                            </v-icon>
                        </v-btn>
                    </v-row>
                </v-list-item>
            </v-card-actions>
        </v-card>
        <v-card
            height=auto
            color="#9FE2BF"
            style="margin: 0px 10px 10px 10px;"
        >
            <v-card-item>
                <v-img
                    cover
                    height="200"
                    src="https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BLACKPINK_1.png?alt=media&token=4faa7b78-c300-497f-be9f-dac62b690449"
                ></v-img>
            </v-card-item>
            <!-- <v-card-text class="text font-weight-bold">
                "Turns out semicolon-less style is easier and safer in TS because most gotcha edge cases are type invalid as well."
            </v-card-text>  -->
            <v-card-actions>
                <v-list-item class="grow">
                    <v-list-item-avatar color="grey darken-3">
                        <v-img
                            class="elevation-6"
                            alt=""
                            src="https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BLACKPINK_1.png?alt=media&token=4faa7b78-c300-497f-be9f-dac62b690449"
                        ></v-img>
                    </v-list-item-avatar>
          
                    <v-list-item-content>
                        <v-list-item-title>Blackpink</v-list-item-title>
                    </v-list-item-content>
        
                    <v-row align="center" justify="end" >
                        <!-- <span class="subheading">Twitter</span> -->
                        
                        <v-btn icon href="/band/calendar">
                            <v-icon large>
                                mdi-calendar-multiselect-outline
                            </v-icon>
                        </v-btn>
                    </v-row>
                </v-list-item>
            </v-card-actions>
        </v-card>
        <v-card
            height=auto
            color="#9FE2BF"
            style="margin: 0px 10px 10px 10px;"
        >
            <v-card-item>
                <v-img
                    cover
                    height="200"
                    src="https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/NTC_Dream_1.png?alt=media&token=1aa19b89-4556-488a-9940-6a976b5e79cb"
                ></v-img>
            </v-card-item>
            <!-- <v-card-text class="text font-weight-bold">
                "Turns out semicolon-less style is easier and safer in TS because most gotcha edge cases are type invalid as well."
            </v-card-text>  -->
            <v-card-actions>
                <v-list-item class="grow">
                    <v-list-item-avatar color="grey darken-3">
                        <v-img
                            class="elevation-6"
                            alt=""
                            src="https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/NTC_Dream_1.png?alt=media&token=1aa19b89-4556-488a-9940-6a976b5e79cb"
                        ></v-img>
                    </v-list-item-avatar>
          
                    <v-list-item-content>
                        <v-list-item-title>NTC Dream</v-list-item-title>
                    </v-list-item-content>
        
                    <v-row align="center" justify="end" >
                        <!-- <span class="subheading">Twitter</span> -->
                        
                        <v-btn icon href="/band/calendar">
                            <v-icon large>
                                mdi-calendar-multiselect-outline
                            </v-icon>
                        </v-btn>
                    </v-row>
                </v-list-item>
            </v-card-actions>
        </v-card>
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
        <v-card height="0" style="margin: 40px;"></v-card>
    </v-container>
    </v-app>
</template>

<script>
    export default {
        middleware: 'auth',
        layout: 'home_layout',
        data () {
            return {
                tags: [
                    'EXO',
                    'TWITCH',
                    'REDELVET',
                    'TREASUR',
                    'NTC DREAM',
                    'SEVENTEEN'
                ],
                items: [
                    {
                        src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BLACKPINK_1.png?alt=media&token=4faa7b78-c300-497f-be9f-dac62b690449',
                    },
                    {
                        src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BLACKPINK_5.png?alt=media&token=cd8307d4-6075-487c-b54b-a3c5f1b7893f',
                    },
                    {
                        src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/BTS_4.png?alt=media&token=05b86144-1dd9-48e2-bfcb-afa49f07d5fb',
                    },
                    {
                        src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/NTC_Dream_4.png?alt=media&token=7c62b943-a524-45ed-ab00-922e51d3078b',
                    },
                    {
                        src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/Red_Velvet_1.png?alt=media&token=2f31435d-088b-4a35-a1c3-6420016eb2fd',
                    },
                    {
                        src: 'https://firebasestorage.googleapis.com/v0/b/yeobo-app.appspot.com/o/TWITCH_3.png?alt=media&token=06030857-7eef-4d59-8b31-1a9e98f43275',
                    },
                ],
            }
        },
    }
</script>