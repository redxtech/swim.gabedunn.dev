<template>
  <table class="table-auto mx-auto">
    <thead>
      <tr class="bg-green-500">
        <th
          v-for="column in columns"
          :key="column"
          class="px-4 py-2"
          v-text="column"
        />
      </tr>
    </thead>
    <tbody class="bg-green-200">
      <swim
        v-for="(event, i) in events"
        :key="`${event.distance}m-${event.stroke}-${event.course}`"
        :event="event"
        :even="i % 2 === 0"
      />
    </tbody>
  </table>
</template>

<script>
  import Swim from './Swim'

  export default {
    name: 'TimesTable',
    components: { Swim },
    data () {
      return {
        columns: [
          'Event',
          'Course',
          'Time',
          '+3%',
          '+5%',
          '+10%',
          '+15%',
          'Status',
          'USports',
          'USports +1.5%',
          'USports +5%',
          'USports +7.5%'
        ],
        events: [
          {
            distance: 50,
            course: 25,
            stroke: 'free',
            time: 24.22
          },
          {
            distance: 50,
            course: 50,
            stroke: 'free',
            time: 24.84
          },
          {
            distance: 100,
            course: 25,
            stroke: 'free',
            time: 52.80
          },
          {
            distance: 100,
            course: 50,
            stroke: 'free',
            time: 54.21
          },
          {
            distance: 50,
            course: 25,
            stroke: 'fly',
            time: 26.32
          },
          {
            distance: 50,
            course: 50,
            stroke: 'fly',
            time: 26.87
          },
          {
            distance: 100,
            course: 25,
            stroke: 'fly',
            time: 57.05
          },
          {
            distance: 100,
            course: 50,
            stroke: 'fly',
            time: 59.27
          }
        ]
      }
    }
  }
</script>
