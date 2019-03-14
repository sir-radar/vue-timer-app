<template>
  <v-app>
    <Navbar/>
    <v-content>
     <Timer :timer="formattedTime" :state="timerState"/>
    </v-content>
  </v-app>
</template>

<script>
import Navbar from './components/Navbar';
import Timer from './components/Timer';

export default {
  name: 'App',
  components: {
    Navbar,
    Timer
  },
  data () {
    return {
      timerState: 'stopped',
      currentTimer: 0,
      formattedTime: "00:00:00",
      ticker: null,
      taps: [],
      lastestLap: "",
      snackbar: false
    }
  }
}
</script>
