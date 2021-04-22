<template lang="">
  <div id="navbar-wrapper">
    <ul id="nav-menu">
      <li class="nav-item"><a href="">Link 1</a></li>
      <li class="nav-item"><a href="">Link 2</a></li>
      <li class="nav-item"><a href="">Link 3</a></li>
      <li class="nav-item"><a href="">Link 4</a></li>
      <li class="nav-item"><a href="">Link 5</a></li>
    </ul>
    <button @click="toggleMatrix" id="matrix-button">Red Pill</button>
  </div>
</template>
<script>
export default {
  methods: {
    toggleMatrix() {
      document.getElementById("c").classList.toggle("hide");
      if (document.getElementById("c").classList.contains("hide")) {
        document.getElementById("matrix-button").innerText = "Red Pill";
        document.getElementById("matrix-button").style.border = "1px solid red";
      } else {
        document.getElementById("matrix-button").innerText = "Blue Pill";
        document.getElementById("matrix-button").style.border =
          "1px solid blue";
      }
    }
  }
};
</script>
<style scoped lang="scss">
#navbar-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 60px;
  position: relative;
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
      }
    }
    .nav-item:hover {
      transform: scale(1.15); //translateY(-3px);
    }
  }
  #matrix-button {
    position: absolute;
    right: 2rem;
    color: #fff;
    // border: 1px solid red;
    border-radius: 1rem;
    padding: 0.5rem 1rem;
    transition: all 0.2s linear;
  }
  #matrix-button:hover {
    letter-spacing: 3px;
  }
}
</style>
