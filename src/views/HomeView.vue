<template>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Poppins">
  <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Molend">
  <div class="theme-bg">
    <Nav v-if="!this.showWebView" open_button_style="icon" open_button_color="white" />
    <div class="graphic">
      <img src="@/assets/images/tedx_iitplogo2023.png" style="height:70px;margin-top:2vh;margin-left:4vh;">
    </div>
    <div class="logo-container">
      <!-- <img src="@/assets/images/newlogo.png" class="logo" style="height:70px;margin-left:40px;margin-top:-10vh;"> -->
      <HomeNav v-if="this.showWebView" style="left: 33.5vw;" />
    </div>

    <!-- <div class="logo-container">
      <img src="@/assets/images/newlogo.png" class="logo" style="height:70px;margin-left:40px;margin-top:-10vh;">
      <HomeNav v-if="this.showWebView" />
    </div> -->
    <!-- <img src="@/assets/images/newlogo.png" class="logo" style="height:70px;margin-left:40px;margin-top:-10vh;"> -->

    <!-- web-view landing -->

    <!-- <section class="landing full" v-if="this.showWebView">
    <div class="black-bg"></div>

    <div class="countdown-container">
      <div class="title">Live in</div>
      <div class="countdown">
        <span id="days">{{ this.formatTime(this.displayDays) }}</span>d
        <span id="hrs">{{ this.formatTime(this.displayHours) }}</span>h
      </div>
    </div>

    <div class="paintedx">
      <img src="@/assets/images/paintedx.png">
    </div>

    <div class="logo-container">
      <img src="@/assets/images/barcode.png" class="barcode">
      <img src="@/assets/images/tedx iitpatna_logo-2B.png" class="logo">
      <HomeNav v-if="this.showWebView" />
    </div>
  </section> -->

    <!-- mobile-view landing -->
    <!--<section class="landing mobile full" v-else>
    <div class="countdown-container">
      <div class="title">Live in</div>
      <div class="countdown">
        <span id="days">{{ this.formatTime(this.displayDays) }}</span> days,
        <span id="hrs">{{ this.formatTime(this.displayHours) }}</span> hours
      </div>
    </div>

    <div class="strokex">
      <img src="@/assets/images/cross_stroke.png">
    </div>

    <img src="@/assets/images/tedx iitpatna_logo-1B.png" class="iitp-logo">
  </section> -->

    <!-- web+mobile view of the theme banner -->
    <!-- <section :class="['theme', 'infaff', this.screenWidth > this.screenHeight * 1.1 ? 'web' : 'mobile']">
    <img src="@/assets/images/infinity-logo.png" class="bg" v-if="this.screenWidth > this.screenHeight * 1.1">
    <img src="@/assets/images/infinity-logo-vertical.png" class="bg" v-else>
    <span class="title">Infinite Affinities</span>
  </section> -->

    <!-- web+mobile view of the contents -->


    <div class="center">

      <div class="gra" > <img src="@/assets/images/TEXT.png"></div>
    </div>



    <section :class="['content-wrapper', 'full', this.screenWidth > 1000 ? 'web' : 'mobile']">

      
      <div class="content">
        <div class="title">What is TEDx?</div>
        <div class="text">In the spirit of ideas worth spreading, TED has created a program called TEDx. TEDx is a
          program
          of local, self-organized events that bring people together to share a TED-like experience. Our event is called
          TEDx IITPatna, where x = independently organized TED event. At our TEDx IITPatna event, TED Talks video and
          live
          speakers will combine to spark deep discussion and connection in a small group. The TED Conference provides
          general guidance for the TEDx program, but individual TEDx events , including ours, are self-organized.</div>
        <a href="https://www.ted.com/about/programs-initiatives/tedx-program" target="_blank" class="link"
          rel="noopener noreferrer">More about TEDx Program</a>
      </div>
      <div class="graphic" id="c"><img src="@/assets/images/Vector.png"></div>
    </section>

    <section :class="['content-wrapper', 'full', this.screenWidth > 1000 ? 'web' : 'mobile']">
      
      <div class="content">
        <div class="title">What is Tedx IITPatna?</div>
        <div class="text">Since 2016 TEDx IITPatna has strived to establish momentous and unforgettable events with
          discussions that have a long-term impact. With a footfall of 1500+ participants in our past events,
          we have continued to promote creativity and spark conversations even amid a global pandemic.
          As we reach a semblance of normalcy, this year, we present our fourth edition - "Infinite Affinities."
          We celebrate symbiosis and the independent yet collaborative spirit that allows us to reach new heights.
          Featuring diverse speakers from various walks of life, we hope to provide an enlightening experience to our
          community.
        </div>
        <router-link to="/about" class="link">Know More</router-link>
      </div>
      <div class="graphic" id="c"><img src="@/assets/images/Group32068.png"></div>
    </section>



  </div>

  <!-- <section :class="['speaker-application', this.screenWidth > 560 ? 'web' : 'mobile']">
    <div class="title">Interested in becoming a speaker?</div>
    <a href="https://forms.gle/jhDwBQmSFid4jjPZ6" target="_blank" class="link">Speaker Applications →</a>
  </section> -->

  <Footer/>
</template>

<script scoped>
// @ is an alias to /src
import Nav from '@/components/Nav.vue'
import HomeNav from '@/components/Home.Nav.vue'
import Footer from '@/components/Footer.vue'

export default {
  name: 'HomeView',
  components: {
    Nav,
    Footer,
    HomeNav,
  },
  data() {
    return {
      screenWidth: window.innerWidth,
      screenHeight: window.innerHeight,
      showWebView: window.innerWidth >= (1.51 * window.innerHeight),

      countdownTarget: new Date("2022-09-03T00:00:00.000+05:30"), // target date for countdown
      displayDays: 0,
      displayHours: 0,
      _days: 60 * 60 * 24,
      _hours: 60 * 60,
    }
  },
  methods: {
    onResize() {
      this.screenWidth = window.innerWidth
      this.screenHeight = window.innerHeight
      this.showWebView = window.innerWidth >= (1.51 * window.innerHeight)
    },
    formatTime(val) {
      return val >= 10 ? String(val) : "0" + String(val)
    },
    countdownLogic(interval) {
      const now = new Date()
      const deltaT = Math.trunc((this.countdownTarget.getTime() - now.getTime()) / 1000) // in seconds

      if (deltaT < 0) {
        // closeInterval(interval)
        return
      }

      const days = Math.trunc(deltaT / this._days)
      const hours = Math.trunc((deltaT - days * this._days) / this._hours)

      this.displayDays = days
      this.displayHours = hours
    }
  },
  created() {
    this.countdownLogic()
    const timer = setInterval(() => this.countdownLogic(timer), 1000)
  },
  mounted() {
    this.$nextTick(() => {
      window.addEventListener('resize', this.onResize)
    })
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.onResize)
  }
}
</script>

<style>
@import '@/assets/css/home.css';
@import '@/assets/css/home.mobile.css';
</style>
<style scoped>
.theme-bg {
  background-image: url('/src/assets/images/Frame40.png');
  overflow-x: hidden;

}
</style>
