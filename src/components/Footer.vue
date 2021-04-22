<template lang="">
  <div id="footer-wrapper">
    <div class="logo-wrapper">
      <img :src="owlLogo" alt="my icon" />
      <p>Proudly presented by <a href="">NightOwl Society</a></p>
    </div>
    <div id="link-grid">
      <ul class="footer-list">
        <li class="footer-list-item first-list-item">
          <a href="">Good Causes</a>
        </li>
        <li class="footer-list-item"><a href="">TreeSisters</a></li>
        <li class="footer-list-item"><a href="">Sea Sheperd</a></li>
        <li class="footer-list-item"><a href="">Frag den Staat</a></li>
      </ul>
      <ul class="footer-list">
        <li class="footer-list-item first-list-item">
          <a href="">Developers</a>
        </li>
        <li class="footer-list-item"><a href="">Link 1</a></li>
        <li class="footer-list-item"><a href="">Link 2</a></li>
        <li class="footer-list-item"><a href="">Link 3</a></li>
      </ul>
      <ul class="footer-list">
        <li class="footer-list-item first-list-item">
          <a href="">Ressources</a>
        </li>
        <li class="footer-list-item"><a href="">Privacy</a></li>
        <li class="footer-list-item"><a href="">Contact</a></li>
      </ul>
      <ul class="footer-list">
        <li class="footer-list-item first-list-item">
          <a href="">Product Help</a>
        </li>
        <li class="footer-list-item"><a href="">Support</a></li>
        <li class="footer-list-item"><a href="">FAQ</a></li>
        <li class="footer-list-item"><a href="">Blog</a></li>
      </ul>
    </div>
    <div id="footer-end">
      <div class="footer-end-wrapper">
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores a
          qui odit sapiente dolores eius voluptatem ullam quibusdam vel numquam
          rem iusto tempore deserunt aliquid corrupti ea cupiditate est fugit
          atque autem sequi officia, vitae magnam. Suscipit ipsam sunt fugiat
          tempora.
        </p>
        <div class="lang-select-wrapper">
          <label for="lang-select">Language: </label>
          <span id="lang-select" class="custom-select">
            <select>
              <option value="0">english</option>
              <option value="1">german</option>
              <option value="2">french</option>
              <option value="3">spanish</option>
              <option value="4">chinese</option>
              <option value="5">japanese</option>
            </select>
          </span>
        </div>
      </div>
      <ul class="footer-end-list">
        <li><a href="">Privacy</a></li>
        <li><a href="">Cookies</a></li>
        <li><a href="">Logo</a></li>
        <li><a href="">Group policy</a></li>
        <li><a href="">Community Guidelines</a></li>
      </ul>
    </div>
  </div>
</template>
<script>
import owlLogo from "@/assets/images/owl-logo.png";
export default {
  data() {
    return {
      owlLogo
    };
  }
};
</script>

<style scoped lang="scss">
@media (min-width: 891px) {
  #footer-wrapper {
    background-color: #111;
    .logo-wrapper {
      display: flex;
      align-items: flex-end;
      padding: 1rem 0;
      width: 75%;
      margin: 0 auto;
      img {
        width: 3rem;
      }
      p {
        color: #bbb;
        margin-left: 1.5rem;
        a {
          text-decoration: none;
          color: #bbb;
          font-weight: 700;
          transition: all 0.3s linear;
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
          height: 2px;
          transform-origin: 0;
          transition: transform 0.2s ease-in-out;
          transition: all 0.2s linear;
        }

        a:hover::after {
          transform: none;
        }
        a:hover {
          color: #fff;
        }
      }
    }
    #link-grid {
      margin: 0 auto;
      max-width: 75%;
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      padding: 1rem 0 3rem 0;
      border-bottom: 1px solid #999;
      .footer-list {
        list-style: none;
        display: flex;
        flex-flow: column;
        .footer-list-item {
          padding: 0.5rem;
          a {
            text-decoration: none;
            color: #bbb;
            transition: all 0.3s linear;
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
            height: 1px;
            transform-origin: 0;
            transition: transform 0.2s ease-in-out;
            transition: all 0.2s linear;
          }

          a:hover::after {
            transform: none;
          }
        }
        .first-list-item {
          border-bottom: 1px solid #888;
          margin-bottom: 1rem;
          max-width: 8rem;
          a {
            font-weight: 600;
            color: #fff;
          }
          a:hover {
            cursor: default;
          }
        }
      }
    }
    #footer-end {
      max-width: 75%;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      .footer-end-wrapper {
        color: #bbb;
        display: grid;
        grid-template-columns: 2fr 1fr;
        align-items: center;
        padding: 2rem 0 0 0;
        .lang-select-wrapper {
          display: flex;
          justify-content: flex-end;
          > * {
            padding: 0 1rem 0 1rem;
          }
          .custom-select {
            position: relative;
            width: 100px;
            background-color: #bbb;
            select {
              display: block; /*hide original SELECT element: */
            }
          }
        }
        p {
          font-size: 0.75rem;
        }
      }
      .footer-end-list {
        list-style: none;
        display: flex;
        justify-content: space-between;
        padding: 2rem 0;
        li {
          a {
            text-decoration: none;
            color: #bbb;
            transition: all 0.3s linear;
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
            height: 1px;
            transform-origin: 0;
            transition: transform 0.2s ease-in-out;
            transition: all 0.2s linear;
          }

          a:hover::after {
            transform: none;
          }
        }
      }
    }
  }
}
@media (max-width: 890px) {
  #footer-wrapper {
    background-color: #111;
    .logo-wrapper {
      display: flex;
      align-items: flex-end;
      padding: 1rem 0;
      width: 75%;
      margin: 0 auto;
      img {
        width: 3rem;
      }
      p {
        color: #bbb;
        margin-left: 1.5rem;
        a {
          text-decoration: none;
          color: #bbb;
          font-weight: 700;
          transition: all 0.3s linear;
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
          height: 2px;
          transform-origin: 0;
          transition: transform 0.2s ease-in-out;
          transition: all 0.2s linear;
        }

        a:hover::after {
          transform: none;
        }
        a:hover {
          color: #fff;
        }
      }
    }
    #link-grid {
      max-width: 80%;
      margin: 0 auto;
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-template-rows: auto;
      border-bottom: 1px solid #999;
      padding-bottom: 3rem;
      .footer-list {
        list-style: none;
        margin: 2rem auto 0;
        .footer-list-item {
          padding: 0.5rem;
          a {
            text-decoration: none;
            color: #bbb;
            transition: all 0.3s linear;
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
            height: 1px;
            transform-origin: 0;
            transition: transform 0.2s ease-in-out;
            transition: all 0.2s linear;
          }

          a:hover::after {
            transform: none;
          }
        }
        .first-list-item {
          border-bottom: 1px solid #888;
          margin-bottom: 1rem;
          max-width: 8rem;
          a {
            font-weight: 600;
            color: #fff;
          }
          a:hover {
            cursor: default;
          }
        }
      }
    }
    #footer-end {
      max-width: 75%;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      .footer-end-wrapper {
        color: #bbb;
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: auto;
        align-items: center;
        padding: 2rem 0 0 0;
        .lang-select-wrapper {
          display: flex;
          justify-content: space-around;
          width: 30%;
          margin: 0 auto;
          padding: 1rem 0;
          label {
            padding: 0 1rem;
          }
          .custom-select {
            position: relative;
            width: 100px;
            background-color: #bbb;
            select {
              display: block; /*hide original SELECT element: */
            }
          }
        }
        p {
          font-size: 0.75rem;
        }
      }
      .footer-end-list {
        list-style: none;
        // display: flex;
        // justify-content: space-between;
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
        grid-auto-rows: 1fr;
        padding: 2rem 0;
        li {
          padding-bottom: 1rem;
          a {
            text-decoration: none;
            color: #bbb;
            transition: all 0.3s linear;
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
            height: 1px;
            transform-origin: 0;
            transition: transform 0.2s ease-in-out;
            transition: all 0.2s linear;
          }

          a:hover::after {
            transform: none;
          }
        }
      }
    }
  }
}
</style>
