<template>
  <div class="clock" v-if="hourtime != ''">
    <div class="clock__hours">
      <span class="clock__hourtime" v-text="hourtime"></span>
      <span v-text="hours"></span>
    </div>
    <div class="clock__minutes" v-text="minutes"></div>
    <div class="clock__seconds" v-text="seconds"></div>
  </div>
</template>

<script>
export const SECOND = 1000;
export const HOUR = 12;

export function getHourTime (h) {
  return h >= 12 ? 'PM' : 'AM'
}

export function getZeroPad (n) {
  return (parseInt(n, 10) >= 10 ? '' : '0') + n
}
export default {
  data() {
    return {
      hours: 0,
      minutes: 0,
      seconds: 0,
      hourtime: '',
    };
  },
  mounted() {
    const timer = window.setTimeout(this.updateDateTime, SECOND);
    this.$on('hook:destroyed', () => window.clearTimeout(timer))
  },
  methods: {
    updateDateTime() {
      const now = new Date();
      this.hours = now.getHours();
      this.minutes = getZeroPad(now.getMinutes());
      this.seconds = getZeroPad(now.getSeconds());
      this.hourtime = getHourTime(this.hours);
      this.hours = this.hours % HOUR || HOUR;
      this.$options.timer = window.setTimeout(this.updateDateTime, SECOND);
    },
  },
};
</script>

<style scoped>
.clock {
  background: rgba(255, 255, 255, 0);
  border: 0.3rem solid rgb(0, 183, 255);
  border-radius: 0.5rem;
  display: flex;
  margin-bottom: 1em;
  margin-top: 1em;
  margin-left: 110px;
  margin-right: 0px;
  box-shadow: 0 0 40px rgba(10, 175, 230, 1),  0 0 20px rgba(10, 175, 230, 0);
}
.clock__hours,
.clock__minutes,
.clock__seconds {
  background: linear-gradient(to bottom, #26303b 50%, #2c3540 50%);
  display: inline-block;
  color: #fff;
  font-family: 'Nunito', sans-serif;
  font-size: 20px;
  
  padding: 0.5rem 1rem;
  text-align: center;
  position: relative;
}
.clock__hours {
  border-right: 0.15rem solid #fff;
  border-radius: 0.5rem 0 0 0.5rem;
}
.clock__minutes {
  border-right: 0.15rem solid #fff;
}
.clock__seconds {
  border-radius: 0 0.5rem 0.5rem 0;
}
.clock__hourtime {
  font-size: 10px;
  position: absolute;
  top: 2px;
  left: 8px;
}
</style>