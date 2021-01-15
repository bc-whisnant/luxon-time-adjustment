<template>
  <div class="hello">
    <ul>
      <li v-for="(time, index) in event" :key="index">
        {{ changeTime(time) }}
      </li>
    </ul>
  </div>
</template>

<script>
import { DateTime } from 'luxon'
export default {
  name: 'HelloWorld',
  data() {
    return {
      date: '',
      event: {
        timeOne: DateTime.local(2021, 2, 4, 5, 30),
        timeTwo: DateTime.local(2020, 4, 20)
      },
      timezone: 'Testing One',
      timezoneTwo: 'Testing Two'
    }
  },
  props: {
    msg: String
  },
  methods: {
    changeTime(time) {
      if (this.timezone === 'Testing') {
        return time.plus({ hours: 2}).toLocaleString(DateTime.TIME_24_SIMPLE)
      }

      if (this.timezoneTwo === 'Testing Two') {
        return time.plus({ hours: 4}).toLocaleString(DateTime.TIME_24_SIMPLE)
      }
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: flex;
  flex-direction: column;
  margin: 10px;
}
a {
  color: #42b983;
}
</style>
