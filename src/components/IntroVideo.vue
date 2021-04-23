<template lang="">
  <section class="showcase">
    <header>
      <h2 class="logo">Title</h2>
      <div class="toggle">
        <ul class="social">
          <li>
            <a href="#"><img :src="fbk" alt=""/></a>
          </li>
          <li>
            <a href="#"><img :src="twttr" alt=""/></a>
          </li>
          <li>
            <a href="#"><img :src="insta" alt=""/></a>
          </li>
        </ul>
      </div>
    </header>

    <video :src="intro" type="video/mp4" muted loop autoplay></video>

    <div class="overlay"></div>

    <div class="text">
      <h2>Never Stop</h2>
      <h3>expecting wonders</h3>
      <p>
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fuga, tenetur.
        Non id officiis, iure deserunt dolor quia, magni cupiditate voluptates
        maiores officia ad repellat tenetur eaque temporibus eveniet adipisci
        perspiciatis!
      </p>
      <a href="#">Click this</a>
      <a
        id="scroll-position-one"
        href="#"
        style="z-index: -999; top: 50vh; position: absolute; background-color: #ffffff00;"
      ></a>
    </div>
  </section>
  <!-- <div id="navbar">
      <Navbar />
    </div> -->
</template>

<script>
//import Navbar from "@/components/Navbar.vue";
import introVideo from "@/assets/videos/intro.mp4";
import facebook from "@/assets/icons/facebook.png";
import twitter from "@/assets/icons/twitter.png";
import instagram from "@/assets/icons/instagram.png";
const intro = introVideo;
const fbk = facebook;
const twttr = twitter;
const insta = instagram;
export default {
  data() {
    return {
      intro,
      fbk,
      twttr,
      insta
    };
  },
  components: {
    //Navbar
  }
};
</script>

<style lang="scss">
#scroll-position-one:hover {
  cursor: default;
}
.showcase {
  //   position: absolute;
  right: 0;
  width: 100%;
  min-height: calc(100vh - 60px);
  padding: 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #777;
  color: #fff;
  z-index: 1;
  transition: 0.5s;
}
.logo {
  text-transform: uppercase;
  cursor: pointer;
}
.showcase header {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  padding: 40px 100px;
  z-index: 2;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.showcase video {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  opacity: 0.8;
}
.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #60481b; /*#03a9f4;*/
  mix-blend-mode: overlay;
}
.text {
  position: relative;
  z-index: 2;
}
.text h2 {
  font-size: 5em;
  font-weight: 800;
  line-height: 1em;
  text-transform: uppercase;
}
.text h3 {
  font-size: 4em;
  font-weight: 700;
  line-height: 1em;
  text-transform: uppercase;
}
.text p {
  font-size: 1.1em;
  margin: 20px 0;
  font-weight: 400;
  max-width: 700px;
}

.text a {
  display: inline-block;
  font-style: 1em;
  background: #fff;
  padding: 10px 30px;
  text-decoration: none;
  color: #111;
  margin-top: 10px;
  text-transform: uppercase;
  letter-spacing: 2px;
  transition: 0.2s;
}
.text a:hover {
  letter-spacing: 6px;
}

.social {
  z-index: 2;
  display: flex;
  justify-content: center;
  align-items: center;
}

.social li {
  list-style: none;
  filter: invert(1);
  margin-right: 20px;
  transform: scale(0.5);
  transition: 0.5s;
}

.social li:hover {
  transform: scale(0.5) translateY(-15px);
}
.toggle {
  position: relative;
  width: 60px;
  height: 60px;
  cursor: pointer;
  left: 0;
}
@media (max-width: 798px) {
  .showcase,
  .showcase header {
    padding: 40px;
  }
  .text h2 {
    font-style: 3em;
  }
  .text h3 {
    font-style: 2em;
  }
  .social {
    margin-right: 80px;
  }
}
</style>
