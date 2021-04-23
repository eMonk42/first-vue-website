<template lang="">
  <div id="global-wrapper">
    <canvas class="hide" id="c"></canvas>
    <div id="intro-video-wrapper">
      <IntroVideo />
    </div>
    <div id="navbar-sticky-check-element"></div>
    <div id="navbar-wrapper">
      <Navbar @updated="say" />
    </div>
    <MainThree />
    <a id="scroll-position-two" href="#"></a>
    <MainOne :changeImage="isOn" />
    <div id="second-main-wrapper">
      <MainTwo />
    </div>
    <Newsletter />
    <a id="scroll-position-three" href="#"></a>
    <Footer />
  </div>
</template>
<script>
import IntroVideo from "../components/IntroVideo";
import Navbar from "@/components/Navbar.vue";
import MainOne from "@/components/MainOne.vue";
import Newsletter from "@/components/Newsletter";
import Footer from "@/components/Footer.vue";
import MainTwo from "@/components/MainTwo.vue";
import MainThree from "@/components/MainThree";
export default {
  data() {
    return {
      isOn: false
    };
  },
  components: {
    IntroVideo,
    Navbar,
    MainOne,
    Newsletter,
    Footer,
    MainTwo,
    MainThree
  },
  computed: {},
  methods: {
    say() {
      console.log("updated got catched");
      this.isOn = !this.isOn;
    },
    play() {
      console.log("catched");
    }
  },
  mounted() {
    //-----------------------------------
    var observer = new IntersectionObserver(
      function(entries) {
        if (entries[0].intersectionRatio === 0)
          document
            .querySelector("#navbar-wrapper")
            .classList.add("navbar-is-sticky");
        // fully intersects with screen
        else if (entries[0].intersectionRatio === 1)
          document
            .querySelector("#navbar-wrapper")
            .classList.remove("navbar-is-sticky");
      },
      {
        threshold: [0, 1]
      }
    );
    observer.observe(document.querySelector("#navbar-sticky-check-element"));
    //-----------------------------------
    const c = document.getElementById("c"); //as HTMLCanvasElement
    const ctx = c.getContext("2d"); //as any
    // console.log(ctx);
    c.height = window.innerHeight;
    c.width = window.innerWidth;
    const txts = "αβγδεζηθικλμνξοπρστυφχψω∷∫∮∝∞∧∨∑∏∪∩∈∵∴⊥‖∠⌒⊙≌√".split("");
    const font_size = 12; //12
    var columns = c.width / font_size;
    var drops = []; //as any

    for (var x = 0; x < columns; x++) drops[x] = 1;

    function draw() {
      ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
      ctx.fillRect(0, 0, c.width, c.height);
      ctx.fillStyle = "#490";
      ctx.font = font_size + "px arial";
      for (var i = 0; i < drops.length; i++) {
        var text = txts[Math.floor(Math.random() * txts.length)];
        ctx.fillText(text, i * font_size, drops[i] * font_size);
        if (drops[i] * font_size > c.height || Math.random() > 0.98)
          drops[i] = 0;
        drops[i]++;
      }
    }
    setInterval(draw, 20); //20
  }
};
</script>
<style lang="scss">
#global-wrapper {
  #c {
    position: fixed;
    z-index: -1;
  }
  .hide {
    opacity: 0;
  }
  #navbar-wrapper {
    position: sticky;
    top: 0;
    transition: all 0.3s linear;
    // border-bottom: 1px solid rgb(201, 77, 32);
  }
  #navbar-sticky-check-element {
    height: 1px;
    z-index: -1;
    margin-top: -1px;
  }
  .navbar-is-sticky {
    color: #fff;
    background-color: #252525;
    z-index: 100;
  }
  #second-main-wrapper {
    background-color: #000;
    padding-bottom: 3rem;
  }
}
</style>
