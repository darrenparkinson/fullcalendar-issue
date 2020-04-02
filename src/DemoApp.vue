<template>
  <div class="demo-app">
    <FullCalendar
      class="demo-app-calendar"
      ref="fullCalendar"
      defaultView="resourceTimelineMonth"
      :header="{
        left: 'prev,next today',
        center: 'title',
        right: ''
      }"
      :plugins="calendarPlugins"
      :events="calendarEvents"
      :resources="resources"
    />
    <FullCalendar
      class="demo-app-calendar"
      ref="fullCalendar"
      defaultView="resourceTimelineMonth"
      :header="{
        left: 'prev,next today',
        center: 'title',
        right: ''
      }"
      :plugins="calendarPlugins"
      :events="calendarEvents"
      :resources="resources"
      :slotLabelFormat="slotlabel"
      slotLabelInterval="24:00"
    />
  </div>
</template>

<script>
import FullCalendar from "@fullcalendar/vue";
import resourceTimelinePlugin from "@fullcalendar/resource-timeline";
export default {
  components: {
    FullCalendar // make the <FullCalendar> tag available
  },
  data: function() {
    return {
      calendarPlugins: [
        // plugins must be defined in the JS
        resourceTimelinePlugin
      ],
      resources: [
        { id: "person1", title: "Person One" },
        { id: "person2", title: "Person Two" },
        { id: "person3", title: "Person Three" }
      ],
      calendarEvents: [
        // initial event data
        {
          resourceId: "person1",
          title: "Event 1",
          start: "2020-04-02T09:00:00Z",
          end: "2020-04-02T13:00:00Z"
        },
        {
          resourceId: "person1",
          title: "Event 2",
          start: "2020-04-02T13:00:00Z",
          end: "2020-04-02T17:00:00Z"
        },
        {
          resourceId: "person2",
          title: "Event 3",
          start: "2020-04-02T09:00:00Z",
          end: "2020-04-02T17:00:00Z"
        }
      ],
      slotlabel: { day: "numeric", weekday: "narrow" }
    };
  },
  methods: {}
};
</script>

<style lang='scss'>
// you must include each plugins' css
// paths prefixed with ~ signify node_modules
@import "~@fullcalendar/core/main.css";
@import "~@fullcalendar/timeline/main.css";
@import "~@fullcalendar/resource-timeline/main.css";

.demo-app {
  font-family: Arial, Helvetica Neue, Helvetica, sans-serif;
  font-size: 14px;
}

.demo-app-calendar {
  margin: 0 auto;
  max-width: 900px;
}

.fc-sat {
  background-color: red;
}
.fc-sun {
  background-color: green;
}
</style>
