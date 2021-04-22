<template lang="">
  <div id="navbar-wrapper">
    <ul id="nav-menu">
      <li class="nav-item"><a href="">Link 1</a></li>
      <li class="nav-item"><a href="">Link 2</a></li>
      <li class="nav-item"><a href="">Link 3</a></li>
      <li class="nav-item"><a href="">Link 4</a></li>
      <li class="nav-item"><a href="">Link 5</a></li>
    </ul>
    <button @click="toggleMatrix" class="matrix-button" id="one">
      Red Pill
    </button>
    <div id="nav-menu-mobile">
      <button
        v-if="showNavbar"
        @click="toggleMatrix"
        class="matrix-button"
        id="two"
      >
        {{ !matrix ? "Red Pill" : "Blue Pill" }}
      </button>
      <ul v-if="showNavbar" id="mobile-menu-list">
        <li class="mobile-menu-list-item"><a href="">Link 1</a></li>
        <li class="mobile-menu-list-item"><a href="">Link 2</a></li>
        <li class="mobile-menu-list-item"><a href="">Link 3</a></li>
        <li class="mobile-menu-list-item"><a href="">Link 4</a></li>
      </ul>
      <img @click="toggleNavbar" :src="showNavbar ? close : open" alt="" />
    </div>
  </div>
</template>
<script>
import open from "@/assets/icons/menu2.png";
import close from "@/assets/icons/close2.png";

let showNavbar = false;
let matrix = false;

export default {
  data() {
    return {
      open,
      close,
      showNavbar,
      matrix
    };
  },
  methods: {
    toggleMatrix() {
      document.getElementById("c").classList.toggle("hide");
      if (document.getElementById("c").classList.contains("hide")) {
        document.querySelector(".matrix-button").innerText = "Red Pill";
        document.querySelector(".matrix-button").style.border = "1px solid red";
        document.getElementById("footer-wrapper").style.backgroundColor =
          "#111";
        document.getElementById("left-image-newsletter").style.opacity =
          "initial";
        document.getElementById("right-image-newsletter").style.opacity =
          "initial";
        document.querySelector(".showcase").style.opacity = "initial";
        document.getElementById("navbar-wrapper").style.opacity = "initial";
        this.matrix = false;
      } else {
        document.querySelector(".matrix-button").innerText = "Blue Pill";
        document.querySelector(".matrix-button").style.border =
          "1px solid blue";
        document.getElementById("footer-wrapper").style.backgroundColor =
          "#33333300";
        document.getElementById("left-image-newsletter").style.opacity = "0.3";
        document.getElementById("right-image-newsletter").style.opacity = "0.3";
        document.querySelector(".showcase").style.opacity = "0.3";
        document.getElementById("navbar-wrapper").style.opacity = "0.5";
        this.matrix = true;
      }
    },
    toggleNavbar() {
      this.showNavbar = !this.showNavbar;
    }
  }
};
</script>
<style scoped lang="scss">
#nav-menu-mobile {
  display: none;
}
#navbar-wrapper {
  z-index: 10;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 60px;
  position: relative;
  transition: all 0.3s linear;
  #nav-menu {
    width: 50%;
    display: flex;
    justify-content: space-around;
    list-style: none;
    .nav-item {
      transition: all 0.2s linear;
      a {
        color: #ddd;
        text-decoration: none;
        font-weight: 600;
        font-size: 1.5rem;
        transition: all 0.4s linear;
        position: relative;
      }
      a::after {
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

      a:hover::after {
        transform: none;
      }
      a:hover {
        letter-spacing: 3px;
        color: #fff;
      }
    }
    .nav-item:hover {
      transform: scale(1.15); //translateY(-3px);
    }
  }
  .matrix-button#one {
    position: absolute;
    right: 2rem;
    color: #fff;
    border-radius: 1rem;
    padding: 0.5rem 1rem;
    transition: all 0.2s linear;
  }
  .matrix-button#one:hover {
    letter-spacing: 3px;
  }
}

@media (max-width: 1150px) {
  #navbar-wrapper #nav-menu {
    width: 75%;
  }
}

@media (max-width: 750px) {
  #navbar-wrapper {
    #nav-menu {
      display: none;
    }
    button {
      display: none;
    }
    #nav-menu-mobile {
      z-index: 10;
      display: initial;
      height: 60px;
      width: 100%;
      display: flex;
      justify-content: flex-end;
      align-items: center;
      position: relative;
      transition: all 0.3s linear;
      #mobile-menu-list {
        display: flex;
        flex-direction: column;
        position: absolute;
        top: 0;
        list-style: none;
        background-color: #424242;
        width: 100%;
        z-index: 2;
        justify-content: center;
        align-items: center;
        li {
          border-bottom: 1px solid #99999955;
          min-width: 50%;
          text-align: center;
          padding: 0.5rem 0;
          a {
            text-decoration: none;
            color: #bbb;
            font-size: 1.5rem;
            transition: all 0.4s linear;
            position: relative;
          }
          a::after {
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

          a:hover::after {
            transform: none;
          }
          a:hover {
            letter-spacing: 3px;
            color: #fff;
          }
        }
      }
      .matrix-button#two {
        display: initial;
        position: absolute;
        left: 2rem;
        color: #fff;
        // border: 1px solid red;
        border-radius: 1rem;
        padding: 0.5rem 1rem;
        transition: all 0.2s linear;
        z-index: 3;
      }
      .matrix-button:hover#two {
        letter-spacing: 3px;
      }
      img {
        width: 2rem;
        margin-right: 1.5rem;
        z-index: 3;
        transition: all 0.3s linear;
      }
    }
  }
}
</style>
