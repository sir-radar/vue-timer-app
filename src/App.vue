<template>
  <v-app>
    <Navbar/>
    <v-content>
     <Timer 
      :timer="formattedTime" 
      :state="timerState"
      @start="start"
      />
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
  },
  methods:{
    start(){
      if(this.timerState !== 'running'){
        this.tick();
        this.timerState = 'running';
      }
      
    },
    tick(){
      this.ticker = setInterval(() => {
        this.currentTimer++;
        this.formattedTime = this.formatTime(this.currentTimer)
      }, 1000)
    },
    formatTime(seconds){
      let measuredTime = new Date(null);
      measuredTime.setSeconds(seconds);
      let MHSTime = measuredTime.toISOString().substr(11, 8);
      return MHSTime;
    }
  }
}
</script>
