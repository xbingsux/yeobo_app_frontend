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

        <div align="center" justify="center" style="margin: 40px 0px 20px 20px">
            <h1>Popular Tags</h1>
        </div>
        <v-card
            height=450px
            color="#26c6da"
            style="margin: 0px 10px 10px 10px;"
        >
            <v-calendar
                ref="calendar"
                v-model="value"
                :weekdays="weekday"
                :type="type"
                :events="events"
                :event-overlap-mode="mode"
                :event-overlap-threshold="30"
                :event-color="getEventColor"
                @change="getEvents"
            ></v-calendar>
        </v-card>
        
        <!--    
            <v-card-actions>
                <h1>Hello</h1>
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
    import moment from 'moment';
    export default {
        middleware: 'auth',
        layout: 'home_layout',
        data: () => ({
            type: 'month',
            types: ['month', 'week', 'day', '4day'],
            mode: 'stack',
            modes: ['stack', 'column'],
            weekday: [0, 1, 2, 3, 4, 5, 6], //จำนวนวันใน 1 week
            value: '',
            events: [],
            colors: ['blue', 'indigo', 'deep-purple', 'cyan', 'green', 'orange', 'grey darken-1'],
            names: ['Meeting', 'Holiday', 'PTO', 'Travel', 'Event', 'Birthday', 'Conference', 'Party'],
        }),
        methods: {
      getEvents ({ start, end }) {
        const events = []

        const min = new Date(`${start.date}T00:00:00`)
        const max = new Date(`${end.date}T23:59:59`)
        const days = (max.getTime() - min.getTime()) / 86400000
        const eventCount = this.rnd(days, days + 5)

        for (let i = 0; i < eventCount; i++) {
          const allDay = this.rnd(0, 3) === 0
          const firstTimestamp = this.rnd(min.getTime(), max.getTime())
          const first = new Date(firstTimestamp - (firstTimestamp % 900000))
          const secondTimestamp = this.rnd(2, allDay ? 288 : 8) * 900000
          const second = new Date(first.getTime() + secondTimestamp)

          events.push({
            name: this.names[this.rnd(0, this.names.length - 1)],
            start: first,
            end: first,
            color: this.colors[this.rnd(0, this.colors.length - 1)],
            timed: !allDay,
          })
        }

        this.events = events
        // this.events.push({
        //     name: "MAYREE",
        //     start: this.$moment.format("YYYY-MM-DD"),
        //     end: this.$moment.add(1,"day").format("YYYY-MM-DD"),
        //     color: 'indigo',
        //     timed: true,
        // })
        console.log("events",events);
        console.log("this.events",this.events);
      },
      getEventColor (event) {
        return event.color
      },
      rnd (a, b) {
        return Math.floor((b - a + 1) * Math.random()) + a
      },
    },
    }
</script>