<template>
  <div>
    <div class="container pt-5 pb-5">
      <div class="row">
        <div class="col-md-3">
          <img src="/static/avatar.png" class="w-50 pb-3" alt=""><br>
          <input type="text" class="mb-1" value="Karma Drupka"> <br>
        </div>
        <div class="col-md-9">
          <!-- Company names <br><br> -->
          <div class="row">
            <div class="col-md-4">
              <input type="checkbox" class="mt-0 mr-2">Google <br>
              <input type="checkbox" class="mr-2">Facebook <br>
              <input type="checkbox" class="mr-2">Microsoft <br>
              <input type="checkbox" class="mr-2">Apple <br>
              <input type="checkbox" class="mr-2">Uber <br>
              <input type="checkbox" class="mr-2">Lyft <br>
            </div>
            <div class="col-md-4">
              <input type="checkbox" class="mr-2">Amazon <br>
              <input type="checkbox" class="mt-0 mr-2">Airbnb <br>
              <input type="checkbox" class="mr-2">LinkedIn <br>
              <input type="checkbox" class="mr-2">SAP <br>
              <input type="checkbox" class="mr-2">Adobe <br>
              <input type="checkbox" class="mr-2">Samsung <br>
            </div>
            <div class="col-md-4">
              <input type="checkbox" class="mt-0 mr-2">Oracle <br>
              <input type="checkbox" class="mr-2">Salesforce <br>
              <input type="checkbox" class="mr-2">Disney <br>
              <input type="checkbox" class="mr-2">Nike <br>
              <input type="checkbox" class="mr-2">Cisco <br>
              <input type="checkbox" class="mr-2">Stripe <br>
            </div>
          </div>
          <hr class="">
          <input type="checkbox" class="mr-2">Select all 
        </div>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <hr>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-md-3">
          {{ resSendApp }} <br>
          Attempts {{ ttlSendApp }} <br><br>
          <button @click="applyToJobs()">Apply to Jobs</button>
        </div>
        <div class="col-md-3">
          {{ resInterview }} <br>
          Attempts {{ ttlInterview }}<br><br>
          <button @click="interview()">Hear back from Interview</button>
        </div>
        <div class="col-md-3">
          {{ resNegotiate }} <br>
          Attempts {{ ttlNegotiate }}<br><br>
          <button @click="negotiate()">Negotiate</button>
        </div>
        <div class="col-md-3">
          {{ resFirstDay }} <br>
          Attempts {{ ttlFirstDay }}<br><br>
          <button @click="goToFirstDay()">Go to first day</button>
        </div>
      </div>
      <div class="row" v-if="wins">
        <div class="col-md-12 text-center"><br><br>
          <h3 class="blinking">
            You are a dancing ROBOT!
          </h3>Total attempts:
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      resSendApp: 'Not Applied',
      ttlSendApp: 0,
      resInterview: 'Not Interviewed',
      ttlInterview: 0,
      resNegotiate: 'Not Negotiated',
      ttlNegotiate: 0,
      resFirstDay: 'No First Day',
      ttlFirstDay: 0,
      wins: false,
    }
  },
  methods: {
    applyToJobs () {
      let rnd = Math.floor((Math.random() * 20) + 1);

      if (rnd !== 1 && this.resSendApp !== 'Accepted!') {
        // rejected
        this.resSendApp = 'Rejected!'
        this.ttlSendApp++
      } else if (rnd === 1 && this.resSendApp !== 'Accepted!') {
        // success
        this.resSendApp = 'Accepted!'
        this.playChaChing()
      }
    },
    interview () {
      let rnd = Math.floor((Math.random() * 20) + 1);

      if (rnd !== 1 && this.resInterview !== 'Accepted!') {
        // rejected
        this.resInterview = 'Rejected!'
        this.ttlInterview++
      } else if (rnd === 1 && this.resInterview !== 'Accepted!') {
        // success
        this.resInterview = 'Accepted!'
        this.playChaChing()
      }
    },
    negotiate () {
      let rnd = Math.floor((Math.random() * 20) + 1);

      if (rnd !== 1 && this.resNegotiate !== 'Accepted!') {
        // rejected
        this.resNegotiate = 'Rejected!'
        this.ttlNegotiate++
      } else if (rnd === 1 && this.resNegotiate !== 'Accepted!') {
        // success
        this.resNegotiate = 'Accepted!'
        this.playChaChing()
      }
    },
    goToFirstDay () {
      let rnd = Math.floor((Math.random() * 20) + 1);

      if (rnd !== 1 && this.resFirstDay !== 'Accepted!') {
        // rejected
        this.resFirstDay = 'Rejected!'
        this.ttlFirstDay++
      } else if (rnd === 1 && this.resFirstDay !== 'Accepted!') {
        // success
        this.resFirstDay = 'Accepted!'

        this.playShazam();
        this.wins = true
      }
    },
    playChaChing () {
      let file = '/static/cha-ching.mp3'
      var audio = new Audio(file);
      audio.play();
    },
    playShazam () {
      let file = '/static/shazam.mp3'
      var audio = new Audio(file);
      audio.play();
    }
  },
}
</script>

<style>
.blinking {
  animation: blink-animation .75s steps(5, start) infinite;
  -webkit-animation: blink-animation .75s steps(5, start) infinite;
}
@keyframes blink-animation {
  to {
    visibility: hidden;
  }
}
@-webkit-keyframes blink-animation {
  to {
    visibility: hidden;
  }
}
</style>
