<template>
  <div class="app">
    <ul class="wrap">
      <li
        class="item"
        v-for="(item, index) in list"
        :key="item.url"
        :style="{
          left: item.style.left + 'px',
        }"
        @mouseenter="mouseenter(index)"
        @mouseleave="mouseleave(index)"
      >
        <img :src="item.url" />
      </li>
    </ul>
  </div>
</template>

<script>
import Img1 from "./images/1.jpg";
import Img2 from "./images/2.jpg";
import Img3 from "./images/3.jpg";
import Img4 from "./images/4.jpg";

const OFFSET = 50;

export default {
  data() {
    return {
      list: [
        {
          url: Img1,
          style: {
            left: 0,
          },
        },

        {
          url: Img2,
          style: {
            left: OFFSET,
          },
        },

        {
          url: Img3,
          style: {
            left: 2 * OFFSET,
          },
        },

        {
          url: Img4,
          style: {
            left: 3 * OFFSET,
          },
        },
      ],
    };
  },

  methods: {
    mouseenter(index) {
      for (let i = 0; i < this.list.length; i++) {
        if (i > index) {
          this.list[i].style.left += 100;
        }
      }
    },

    mouseleave(index) {
      for (let i = 0; i < this.list.length; i++) {
        if (i > index) {
          this.list[i].style.left -= 100;
        }
      }
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

.app {
  padding: 200px;
}

.wrap {
  width: 500px;
  height: 178.56px;
  list-style: none;
  position: relative;
}

.item {
  position: absolute;
  width: 350px;
  top: 0;
  transition: all 0.3s;
  height: 100%;
  cursor: pointer;
}

.item img {
  vertical-align: middle;
  width: 100%;
  height: 100%;
}
</style>
