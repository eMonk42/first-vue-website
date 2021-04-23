<template lang="">
  <div id="main-two-wrapper">
    <div id="listOne" class="main-two-list">
      <div class="list-head">
        <h3>List One</h3>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
      </div>
      <div class="list-body">
        <ul>
          <li v-for="(item, index) of listOne" :key="index">
            <div class="list-row">
              <p>{{ item.track }}</p>
              <div class="img-wrapper">
                <img :src="item.img" alt="" />
                <i class="fas fa-play-circle"></i>
              </div>
              <h4>
                {{ item.title }}
                <p>{{ item.des }}</p>
              </h4>
              <p class="length">{{ item.length }}</p>
              <i class="fas fa-ellipsis-h"></i>
            </div>
          </li>
        </ul>
      </div>
      <a href="#">See more ...</a>
    </div>

    <div id="listTwo" class="main-two-list">
      <div class="list-head">
        <h3>List Two</h3>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
      </div>
      <div class="list-body">
        <ul>
          <li v-for="(item, index) of listTwo" :key="index">
            <div class="list-row">
              <p>{{ item.track }}</p>
              <div class="img-wrapper">
                <img :src="item.img" alt="" />
                <i class="fas fa-play-circle"></i>
              </div>
              <h4>
                {{ item.title }}
                <p>{{ item.des }}</p>
              </h4>
              <p class="length">{{ item.length }}</p>
              <i class="fas fa-ellipsis-h"></i>
            </div>
          </li>
        </ul>
      </div>
      <a href="#">See more ...</a>
    </div>
  </div>
</template>
<script>
import img01 from "@/assets/images/l0101.png";
import img02 from "@/assets/images/l0102.png";
import img03 from "@/assets/images/l0103.png";
import img04 from "@/assets/images/l0104.png";
import img05 from "@/assets/images/l0105.png";
import img06 from "@/assets/images/l0106.png";
import img07 from "@/assets/images/l0201.png";
import img08 from "@/assets/images/l0202.png";
import img09 from "@/assets/images/l0203.png";
import img10 from "@/assets/images/l0204.png";
import img11 from "@/assets/images/l0205.png";
import img12 from "@/assets/images/l0206.png";
const listOne = [
  {
    img: img01,
    track: "01",
    title: "title",
    des: "further description",
    length: "03:22"
  },
  {
    img: img02,
    track: "02",
    title: "title",
    des: "further description",
    length: "03:22"
  },
  {
    img: img03,
    track: "03",
    title: "title",
    des: "further description",
    length: "03:22"
  },
  {
    img: img04,
    track: "04",
    title: "title",
    des: "further description",
    length: "03:22"
  },
  {
    img: img05,
    track: "05",
    title: "title",
    des: "further description",
    length: "03:22"
  },
  {
    img: img06,
    track: "06",
    title: "title",
    des: "further description",
    length: "03:22"
  }
];
const listTwo = [
  {
    img: img07,
    track: "01",
    title: "title",
    des: "further description",
    length: "03:22"
  },
  {
    img: img08,
    track: "02",
    title: "title",
    des: "further description",
    length: "03:22"
  },
  {
    img: img09,
    track: "03",
    title: "title",
    des: "further description",
    length: "03:22"
  },
  {
    img: img10,
    track: "04",
    title: "title",
    des: "further description",
    length: "03:22"
  },
  {
    img: img11,
    track: "05",
    title: "title",
    des: "further description",
    length: "03:22"
  },
  {
    img: img12,
    track: "06",
    title: "title",
    des: "further description",
    length: "03:22"
  }
];
export default {
  data() {
    return {
      listOne,
      listTwo
    };
  }
};
</script>
<style scoped lang="scss">
#main-two-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  max-width: 75%;
  margin: 0 auto;
  color: #888;
  background-color: #151524ad;
  border-radius: 1rem;
  padding: 1rem;
  .main-two-list {
    padding: 1.5rem 1rem;
    position: relative;
    .list-head {
      //   border: 1px solid magenta;
      h3 {
        color: #fff;
      }
      p {
        padding: 1rem 0;
        font-size: 0.8125rem;
      }
    }
    a {
      text-decoration: none;
      color: #888;
      position: absolute;
      bottom: 0;
      right: 1rem;
      transition: all 0.4s linear;
      //   border: 1px solid magenta;
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
    a:hover {
      color: #fff;
    }
    .list-body {
      //   border: 1px solid gold;
      display: flex;
      padding-bottom: 0.5rem;
      ul {
        width: 100%;
        list-style: none;
        li {
          border-bottom: 1px solid #444;
          .list-row {
            // border: 1px solid green;
            display: flex;
            justify-content: flex-start;
            align-items: center;
            transition: all 0.1s linear;
            h4 {
              color: #fff;
              p {
                font-size: 0.75rem;
                font-weight: 400;
                color: #888;
              }
            }
            .img-wrapper {
              position: relative;
              img {
                max-width: 4rem;
                padding: 0.5rem;
              }
              i {
                position: absolute;
                top: 20px;
                left: 36px;
                color: #fff;
                opacity: 0;
                font-size: 1.5rem;
                text-shadow: 1px 1px #000000aa;
              }
              i:hover {
                opacity: 1;
              }
            }
            .length {
              margin-left: auto;
            }
            .fa-ellipsis-h {
              color: #ccc;
              transition: all 0.2s linear;
              max-width: 2rem;
              margin-right: 1rem;
            }
            .fa-ellipsis-h:hover {
              font-size: 1.75rem;
            }
            i:hover {
              cursor: pointer;
            }
          }
          .list-row > * {
            padding: 0 1rem;
          }
          .list-row:hover {
            transform: scale(1.025);
            background-color: #ffffff11;
            color: rgb(201, 77, 32);
          }
        }
      }
    }
  }
}
@media (max-width: 1150px) {
  #main-two-wrapper {
    grid-template-columns: 1fr;
    grid-auto-rows: 1fr;
  }
}
@media (max-width: 620px) {
  #main-two-wrapper {
    grid-template-columns: 1fr;
    grid-auto-rows: 1fr;
    max-width: 100%;
  }
}
@media (max-width: 470px) {
  #main-two-wrapper {
    grid-template-columns: 1fr;
    grid-auto-rows: 1fr;
    max-width: 100%;
    .main-two-list {
      padding: 1.5rem 0;
      .list-body {
        ul {
          li {
            .list-row > * {
              padding: 0 0.5rem;
            }
          }
        }
      }
    }
  }
}
@media (max-width: 430px) {
  #main-two-wrapper {
    grid-template-columns: 1fr;
    grid-auto-rows: 1fr;
    max-width: 100%;
    .main-two-list {
      padding: 1.5rem 0;
    }
  }
}
</style>
