<template>
  <div>
     <!-- v-if="showRobot"  -->
    <div v-if="showRobot" class="z-index-10000 position-fixed h-100 bg-dark w-100 d-flex justify-content-center align-items-center z-index-100 no-select">
      <div class="bg-white pb-4">
        <img src="/static/giphy.gif" class="noselect" alt="">
        <div class="text-center noselect z-index-10000">
          <br>
          <h3 class="blinking">
            You are a dancing ROBOT!
          </h3>
          Total attempts: {{ ttlApps }} <br><br>
          <div @click="startOver()" class="fake-link">
            Start Over.
          </div>
        </div>
      </div>
    </div>
    <div class="container pt-5 pb-5">
      <div class="row">
        <div class="col-md-3 text-center">
          <img src="/static/avatar.png" class="noselect w-50 pb-3" alt=""><br>
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
        <div class="col-md-3 pb-4">
          {{ resSendApp }} <br>
          Attempts {{ ttlSendApp }} <br><br>
          <button @click="applyToJobs()">Apply to Jobs</button>
        </div>
        <div class="col-md-3 pb-4">
          {{ resInterview }} <br>
          Attempts {{ ttlInterview }}<br><br>
          <button @click="interview()">Hear back from Interview</button>
        </div>
        <div class="col-md-3 pb-4">
          {{ resNegotiate }} <br>
          Attempts {{ ttlNegotiate }}<br><br>
          <button @click="negotiate()">Negotiate</button>
        </div>
        <div class="col-md-3 pb-4">
          {{ resFirstDay }} <br>
          Attempts {{ ttlFirstDay }}<br><br>
          <button @click="goToFirstDay()">Go to first day</button>
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
      showRobot: false,
    }
  },
  computed: {
    ttlApps: function () {
      return this.ttlSendApp + this.ttlInterview + this.ttlNegotiate + this.ttlFirstDay
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
        this.ttlSendApp++

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
        this.ttlInterview++

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
        this.ttlNegotiate++

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
        this.ttlFirstDay++

        this.playShazam();
        this.toggleRobot();
        this.wins = true
      }
    },
    toggleRobot () {
      this.showRobot = !this.showRobot
    },
    startOver () {
      this.showRobot = false

      this.ttlSendApp = 0
      this.ttlApps = 0
      this.ttlInterview = 0
      this.ttlNegotiate = 0
      this.ttlFirstDay = 0
      this.resSendApp = 'Not Applied'
      this.resInterview = 'Not Interviewed'
      this.resNegotiate = 'Not Negotiated'
      this.resFirstDay = 'No First Day'
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
.bg-dark {
  background: rgba(0, 0, 0, .05) !important;
}

.z-index-100 {
  z-index: 100;
}

.z-index-10000 {
  z-index: 10000;
}

.fake-link:hover {
  cursor: pointer;
}

.noselect {
  -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
     -khtml-user-select: none; /* Konqueror HTML */
       -moz-user-select: none; /* Firefox */
        -ms-user-select: none; /* Internet Explorer/Edge */
            user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome and Opera */
}

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
