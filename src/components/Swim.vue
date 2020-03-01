<template>
  <tr :class="{ 'bg-green-300': even }">
    <td v-text="name" />
    <td>{{ event.course }}m</td>
    <td
      class="font-bold"
      v-text="display(convert(event.time, 0))"
    />
    <td v-text="display(convert(event.time, 3))" />
    <td v-text="display(convert(event.time, 5))" />
    <td v-text="display(convert(event.time, 10))" />
    <td v-text="display(convert(event.time, 15))" />
    <td v-if="event.time <= us">
      ✅
    </td>
    <td v-else>
      +{{ round(((event.time / us) - 1) * 100, 1) }}%
    </td>
    <td v-text="display(convert(usports[event.course][event.stroke][event.distance], 0))" />
    <td v-text="display(convert(usports[event.course][event.stroke][event.distance], 1.5))" />
    <td v-text="display(convert(usports[event.course][event.stroke][event.distance], 5))" />
    <td v-text="display(convert(usports[event.course][event.stroke][event.distance], 7.5))" />
  </tr>
</template>

<script>
  export default {
    name: 'Swim',
    props: {
      even: {
        type: Boolean,
        required: false,
        default: false
      },
      event: {
        type: Object,
        required: true,
        validator: val => val &&
          Object.prototype.hasOwnProperty.call(val, 'distance') &&
          Object.prototype.hasOwnProperty.call(val, 'course') &&
          Object.prototype.hasOwnProperty.call(val, 'stroke') &&
          Object.prototype.hasOwnProperty.call(val, 'time')
      }
    },
    data () {
      return {
        usports: {
          25: {
            free: {
              50: 23.16,
              100: 50.54
            },
            fly: {
              50: 24.90,
              100: 55.09
            }
          },
          50: {
            free: {
              50: 23.86,
              100: 52.06
            },
            fly: {
              50: 25.65,
              100: 56.74
            }
          }
        }
      }
    },
    computed: {
      name () { return `${this.event.distance} ${this.capitalize(this.event.stroke)}` },
      us () { return this.usports[this.event.course][this.event.stroke][this.event.distance] }
    },
    methods: {
      capitalize: word => `${word[0].toUpperCase()}${word.slice(1)}`,
      round: (val, n) => Number(Math.round(val + 'e' + n) + 'e-' + n),
      convert (time, percent) { return this.round(time * (1 + (percent / 100)), 2) },
      display (number) {
        const seconds = number % 60
        const mins = Math.floor(number / 60)
        const padding = seconds < 10 ? '0' : ''
        return mins > 0 ? `${mins}:${padding}${seconds.toFixed(2)}` : `${padding}${seconds.toFixed(2)}`
      }
    }
  }
</script>
