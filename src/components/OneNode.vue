<template>
  <div class="main">
    <div class="head">
      <h1>{{ title }} : {{ subtitle }}</h1>
    </div>
    <div class="masonry">
      <template v-for="item in myJSON">
        <div class="masonry-item" :key="item.class">
          <div class="masonry-item-header demibold">
            <span class="medium-font">{{ item.class }}</span>
            <br />
            <span class="medium-small-font italic">{{ item["class-ru"] }}</span>
          </div>
          <router-link :key="item.class" :to="'/class/' + item.class">
            <img
              :alt="item.class"
              :src="imgPath('thumbs/1node/' + item.id + '.jpg')"
              class="thumb"
            />
          </router-link>
          <br />
          <div class="masonry-item-text small-font">
            {{ itemCaption(item) }}
            <br />
            <span class="italic">{{ itemCaptionRu(item) }}</span>
          </div>
        </div>
      </template>
    </div>
  </div>
</template>

<script lang="ts">
import json from "@/json/1nodes.json";

export default {
  name: "herbarium-collection",
  props: {
    options: {
      type: Object,
    },
  },
  data(): {
    title: string;
    subtitle: string;
    myJSON: (
      | {
          id: string;
          "name-ru": string;
          name: string;
          cultivar: string;
          genus: string;
          "genus-ru": string;
          family: string;
          "family-ru": string;
          order: string;
          "order-ru": string;
          class: string;
          "class-ru": string;
          path: string;
        }
      | {
          id: string;
          "name-ru": string;
          name: string;
          genus: string;
          "genus-ru": string;
          family: string;
          "family-ru": string;
          order: string;
          "order-ru": string;
          class: string;
          "class-ru": string;
          path: string;
          cultivar?: undefined;
        }
    )[];
  } {
    return {
      title: "Herbarium INFO",
      subtitle: "Classes",
      myJSON: json,
    };
  },
  methods: {
    imgPath: function (path: string): unknown {
      return require("@/" + path);
    },
    itemCaption: (
      item:
        | {
            id: string;
            "name-ru": string;
            name: string;
            cultivar: string;
            genus: string;
            "genus-ru": string;
            family: string;
            "family-ru": string;
            order: string;
            "order-ru": string;
            class: string;
            "class-ru": string;
            path: string;
          }
        | {
            id: string;
            "name-ru": string;
            name: string;
            genus: string;
            "genus-ru": string;
            family: string;
            "family-ru": string;
            order: string;
            "order-ru": string;
            class: string;
            "class-ru": string;
            path: string;
            cultivar?: undefined;
          }
    ): string => `${item.family} / ${item.genus} / ${item.name}`,
    itemCaptionRu: (
      item:
        | {
            id: string;
            "name-ru": string;
            name: string;
            cultivar: string;
            genus: string;
            "genus-ru": string;
            family: string;
            "family-ru": string;
            order: string;
            "order-ru": string;
            class: string;
            "class-ru": string;
            path: string;
          }
        | {
            id: string;
            "name-ru": string;
            name: string;
            genus: string;
            "genus-ru": string;
            family: string;
            "family-ru": string;
            order: string;
            "order-ru": string;
            class: string;
            "class-ru": string;
            path: string;
            cultivar?: undefined;
          }
    ): string =>
      `${item["family-ru"]} / ${item["genus-ru"]} / ${item["name-ru"]}`,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
body {
  font-size: 150%;
}
.main {
  max-width: 1600px;
  text-align: center;
  margin: 0 auto;
}
.img {
  text-align: center;
}
h1,
h2,
h3,
h4,
h5,
h6 {
  text-align: center;
}
.masonry-item {
  display: inline-block;
  position: relative;
  width: 512px;
  height: 384px;
  padding: 5px;
}
.masonry-item-header {
  color: white;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 5px;
  margin: 5px;
  position: absolute;
  top: 5px;
  left: 5px;
  text-align: left;
}
.masonry-item-text {
  color: white;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 5px;
  margin: 5px;
  position: absolute;
  bottom: 5px;
  right: 5px;
  text-align: right;
}
.item {
  padding-bottom: 100px;
}
.grid {
  display: grid;
}
.right {
  text-align: right;
}
a {
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}
.margin2 {
  margin: 2%;
  vertical-align: top;
}
.icon {
  vertical-align: middle;
  margin: 0.4%;
}
.thumb {
  background-color: #ebebeb;
  width: 512px;
  height: 384px;
}
.masonry {
  display: block;
  text-align: center;
}
.medium-font {
  font-size: 120%;
}
.medium-small-font {
  font-size: 100%;
}
.small-font {
  font-size: 85%;
}
.italic {
  font-style: italic;
}
.demi-bold {
  font-weight: 600;
}
</style>
