<template>
  <div id="app">
    <h1>Vue Scheduler</h1>

    <p>
      The Vue Scheduler allows you to display events in a day along a horizontal
      timeline. Given below is a demonstration.
    </p>

    <br />
    <br />

    <vue-day-schedule
      :events="eventList"
      v-on:vs-date-change="handleDateChange"
    />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import VueDaySchedule from "./components/VueDaySchedule.vue";
import moment from "moment";

@Component({
  components: {
    VueDaySchedule
  }
})
export default class App extends Vue {
  private eventList = [
    {
      name: "Test Event 1",
      date: new Date()
    },
    {
      name: "Test Event 2",
      date: new Date()
    },
    {
      name: "Test Event 3",
      date: moment(new Date())
        .add(30, "minutes")
        .toDate()
    },
    {
      name: "Test Event 4",
      date: moment(new Date())
        .add(120, "minutes")
        .toDate()
    },
    {
      name: "Test Event 5",
      date: moment(new Date())
        .subtract(30, "minutes")
        .toDate()
    },
    {
      name: "Test Event - Really Long Name",
      date: moment(new Date())
        .subtract(220, "minutes")
        .toDate()
    }
  ];

  public handleDateChange(date: Date) {
    //Code to fetch next batch of data based on date can be written here.
    this.eventList = [
      {
        name: "Test Event On Date Change 1",
        date: moment(date)
          .add(120, "minutes")
          .toDate()
      },
      {
        name: "Test Event On Date Change 2",
        date: moment(date)
          .subtract(30, "minutes")
          .toDate()
      }
    ];
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding: 0 15px;
  max-width: 1280px;
  margin: 0 auto;
}
</style>
