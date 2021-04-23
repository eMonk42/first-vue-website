<template lang="">
  <div class="main-three-wrapper">
    <div class="slider-container">
      <div
        class="slide"
        v-for="(image, index) of images"
        :key="index"
        @touchstart="touchStart($event, index)"
        @touchend="touchEnd"
        @touchmove="touchMove($event)"
        @mousedown="touchStart($event, index)"
        @mouseup="touchEnd"
        @mouseleave="touchEnd"
        @mousemove="touchMove($event)"
      >
        <img @dragstart.prevent="preventDef" :src="image.img" alt="" />
        <div class="img-text">
          <h1>{{ image.title }}</h1>
          <h4>{{ image.text }}</h4>
          <a href="#" class="btn">{{ image.link }}</a>
        </div>
      </div>
    </div>
    <div class="left-container">
      <h2>Some quote</h2>
      <h3>And even more text</h3>
      <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vitae
        accusamus alias eaque harum rerum illum aperiam eos ipsa nobis minus?
      </p>
    </div>
  </div>
</template>
<script>
import s01 from "@/assets/images/s01.png";
import s02 from "@/assets/images/s02.png";
import s03 from "@/assets/images/s03.png";
import s04 from "@/assets/images/s04.png";
import s05 from "@/assets/images/s05.png";
import s06 from "@/assets/images/s06.png";
import s07 from "@/assets/images/s07.png";

const images = [
  {
    img: s01,
    title: "Title",
    text: "Grab and drag me!",
    link: "www.url.org"
  },
  {
    img: s02,
    title: "Title",
    text: "Grab and drag me!",
    link: "www.url.org"
  },
  {
    img: s03,
    title: "Title",
    text: "Grab and drag me!",
    link: "www.url.org"
  },
  {
    img: s04,
    title: "Title",
    text: "Grab and drag me!",
    link: "www.url.org"
  },
  {
    img: s05,
    title: "Title",
    text: "Grab and drag me!",
    link: "www.url.org"
  },
  {
    img: s06,
    title: "Title",
    text: "Grab and drag me!",
    link: "www.url.org"
  },
  {
    img: s07,
    title: "Title",
    text: "Grab and drag me!",
    link: "www.url.org"
  }
];
let isDragging = false;
let startPos = 0;
let currentTranslate = 0;
let prevTranslate = 0;
let animationID = 0;
let currentIndex = 0;

export default {
  data() {
    return {
      images,
      isDragging,
      startPos,
      currentTranslate,
      prevTranslate,
      animationID,
      currentIndex
    };
  },
  methods: {
    setSliderPosition() {
      // console.log("setSliderPosition");
      document.querySelectorAll(".slide").forEach(slide => {
        slide.style.transform = `translateX(${this.currentTranslate}px)`;
      });
    },
    setPositionByIndex() {
      // console.log("setPositionByIndex");
      this.currentTranslate =
        this.currentIndex *
        -document.querySelector(".slider-container").clientWidth; //-window.innerWidth;
      this.prevTranslate = this.currentTranslate;
      this.setSliderPosition();
    },
    touchStart(event, index) {
      // console.log("touchStart");
      // console.log("touchStart called me");
      this.currentIndex = index;
      this.startPos = this.getPositionX(event);
      this.isDragging = true;

      this.animationID = requestAnimationFrame(this.animation);

      document.querySelector(".slider-container").classList.add("grabbing");
    },
    touchEnd() {
      // console.log("touchEnd");
      this.isDragging = false;
      cancelAnimationFrame(this.animationID);

      const movedBy = this.currentTranslate - this.prevTranslate;

      if (movedBy < -150 && this.currentIndex < this.images.length - 1) {
        //200
        this.currentIndex += 1;
      } else if (movedBy > 150 && this.currentIndex > 0) {
        this.currentIndex -= 1;
      }

      this.setPositionByIndex();

      document.querySelector(".slider-container").classList.remove("grabbing");
    },
    touchMove(event) {
      // console.log("touchMove");
      if (this.isDragging) {
        const currentPosition = this.getPositionX(event);
        this.currentTranslate =
          this.prevTranslate + currentPosition - this.startPos;
      }
    },
    getPositionX(event) {
      // console.log("getPositionX");
      return event.type.includes("mouse")
        ? event.pageX
        : event.touches[0].clientX;
    },
    animation() {
      // console.log("animation");
      this.setSliderPosition();
      if (this.isDragging) {
        requestAnimationFrame(this.animation);
      }
    },
    preventDef(e) {
      // console.log("preventDefault");
      e.preventDefault();
    }
  }
};
</script>
<style scoped lang="scss">
.main-three-wrapper {
  overflow: hidden;
  // background-color: #333;
  background-image: linear-gradient(140deg, rgb(201, 77, 32), #000);
  width: 100%;
  height: 100%;
  display: grid;
  grid-template-columns: 2fr 3fr;
  .left-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-end;
    color: #bbb;
    padding: 0 3rem;
    h2 {
      text-transform: uppercase;
      font-weight: 800;
      font-size: 3rem;
    }
    h3 {
      font-size: 2rem;
      font-weight: 800;
      text-transform: uppercase;
    }
    p {
      padding: 1rem 0;
      font-weight: 600;
    }
  }
  .slider-container {
    overflow: hidden;
    color: #fff;
    display: inline-flex;
    transform: translateX(0);
    transition: transform 0.3s ease-out;
    // border: 1px solid magenta;
    .slide {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      // padding: 1rem;
      user-select: none;
      min-width: var(--slider-width); //calc(40vw - 7px);
      position: relative;
      background-color: #222;
      transition: all 0.3s ease-in-out;
      img {
        max-width: 100%;
        max-height: 100%;
        transition: transform 0.3s ease-out;
        cursor: grab;
      }
      .img-text {
        position: absolute;
        top: 2rem;
        display: flex;
        color: #111;
        flex-direction: column;
        height: inherit;
        // border: 1px solid blue;
        align-items: center;
        justify-content: center;
        h1 {
          font-size: 2.4rem;
          margin-bottom: 0.5rem;
          font-weight: 800;
          text-transform: uppercase;
          letter-spacing: 3px;
          background-color: #ffffff99;
          padding: 0.5rem;
          box-shadow: 2px 2px #88888855;
          // border: 1px solid red;
          transition: all 0.5s linear;
        }
        h1:hover {
          letter-spacing: 7px;
        }
        h4 {
          font-weight: 800;
          background-color: #ffffff99;
          padding: 0.5rem;
          box-shadow: 2px 2px #88888855;
          // border: 1px solid gold;
          transition: all 0.5s linear;
        }
        h4:hover {
          letter-spacing: 1px;
        }
        .btn {
          color: #111;
          text-decoration: none;
          margin-top: auto;
          // border: 1px solid green;
          transition: all 0.4s linear;
          position: relative;
          letter-spacing: 1px;
          font-weight: 400;
          background-color: #ffffff99;
          padding: 0.5rem;
          margin-top: 0.25rem;
          box-shadow: 2px 2px #88888855;
        }
        .btn::after {
          content: "";
          position: absolute;
          bottom: 0;
          left: 0;
          right: 0;
          background-color: rgb(201, 77, 32);
          transform: scaleX(0);
          height: 3px;
          transform-origin: 0;
          transition: transform 0.2s ease-in-out;
          transition: all 0.2s linear;
        }

        .btn:hover::after {
          transform: none;
        }
      }
    }
  }
}
@media (max-width: 920px) {
  .main-three-wrapper {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr;
    .slider-container {
      .slide {
        min-width: 100vw;
        position: relative;
        height: 100%;
        //border: 1px solid green;
        img {
          max-width: 100vw;
          min-width: 100vw;
          width: 100vw;
        }
        .img-text {
          position: absolute;
          top: 0;
          * {
            transform: scale(0.7);
          }
          h1:hover {
            letter-spacing: 3px;
          }
          h4:hover {
            letter-spacing: 0px;
          }
        }
      }
    }
  }
}
</style>
