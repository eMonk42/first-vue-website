<template lang="">
  <div id="main-one-wrapper">
    <div class="description-wrapper">
      <h3>Things I want you to know about</h3>
      <p>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Doloribus
        natus amet id!
      </p>
      <i class="fas fa-chevron-right"></i>
    </div>
    <div class="gallery-wrapper">
      <div v-for="(game, index) of games" :key="index" class="img-wrapper">
        <img :src="game.img" alt="" />
        <div class="img-text">
          <h5>{{ game.title }}</h5>
          <p>{{ game.description }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import cover01 from "@/assets/images/cover001.jpg";
import cover02 from "@/assets/images/cover002.jpg";
import cover03 from "@/assets/images/cover003.jpg";
import cover04 from "@/assets/images/cover004.jpg";
import cover05 from "@/assets/images/cover005.jpg";
import cover06 from "@/assets/images/cover006.jpg";

//import imgBg from "../assets/images/img-gallery-bg.png";

const games = [
  {
    title: "Civilization V",
    img: cover01,
    description: "Supreme turn-based strategy game"
  },
  {
    title: "Dark Souls",
    img: cover02,
    description: "Fun and challenging. Prepare to die"
  },
  {
    title: "Hades",
    img: cover03,
    description:
      "Action-pased game with amazing voiceactors and beautiful music"
  },
  {
    title: "StarWars KotoR",
    img: cover04,
    description: "Classic RPG and one of Bioware's best"
  },
  {
    title: "Titanfall 2",
    img: cover05,
    description: "Most fun Singleplayer Ego-Shooter ever"
  },
  {
    title: "XCOM Chimera Squad",
    img: cover06,
    description: "Very tactical and very fun"
  }
];
export default {
  data() {
    return {
      games
      //imgBg
    };
  }
};
</script>
<style lang="scss">
#main-one-wrapper {
  background-image: url("../assets/images/img-gallery-bg.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  display: flex;
  flex-direction: column;
  min-width: 80vw;
  min-height: 80vh;
  border-top: 2px solid #00000099;
  .description-wrapper {
    margin: auto auto 0 auto;
    display: flex;
    flex-direction: column;
    position: relative;
    padding: 2rem;
    color: #bbb;
    width: 75%;
    h3 {
      margin-bottom: 1rem;
    }
    i {
      position: absolute;
      right: 2rem;
      bottom: 2rem;
      transition: all 0.2s linear;
    }
    i:hover {
      cursor: pointer;
      transform: scale(1.5);
      color: #fff;
    }
  }
  .gallery-wrapper {
    display: flex;
    justify-content: space-evenly;
    margin: 1rem auto auto auto;
    width: 75%;
    .img-wrapper {
      position: relative;
      display: flex;
      justify-content: space-between;
      transition: all 0.2s linear;
      .img-text {
        position: absolute;
        bottom: 0;
        left: 0;
        background-color: #222222dd;
        padding: 1rem;
        min-height: 8rem;
        transition: all 0.5s linear;
        h5 {
          color: #bbb;
          font-size: 1.25rem;
          font-weight: 600;
          transition: all 0.5s linear;
        }
        p {
          color: #bbb;
          font-size: 0.75rem;
          padding-top: 1rem;
          transition: all 0.5s linear;
        }
      }
      .img-text:hover {
        h5 {
          color: #fff;
        }
        p {
          color: #fff;
        }
      }
      img {
        object-fit: cover;
        width: 200px;
      }
    }
    .img-wrapper:hover {
      transform: scale(1.1);
      cursor: pointer;
    }
  }
}
</style>
