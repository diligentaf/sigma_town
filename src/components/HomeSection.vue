<template>
  <section id="">
    <v-container fluid id="features" class="mt-2 cardColor">
      <v-row align="center" justify="center">
        <v-col cols="10">
          <h1 class="text-center pt-6 font-weight-light display-3 white--text cardColor font-weight-bold">Networks Running</h1>
          <br/> <br/>
          <v-row align="center" justify="space-around">
            <v-col
              cols="12"
              sm="4"
              class="text-center"
              v-for="(feature, i) in features"
              :key="i"
            >
              <v-hover v-slot:default="{ hover }">
                <v-card
                  class="card cardColor"
                  shaped
                  :elevation="hover ? 10 : 4"
                  :class="{ up: hover }"
                >
                  <v-img
                    :src="feature.img"
                    max-width="100px"
                    class="d-block ml-auto mr-auto"
                    :class="{ 'zoom-effect': hover }"
                  ></v-img>
                  <h1 class="font-weight-regular">
                    <!-- {{ feature.title }} -->
                  </h1>
                  <h4 class="font-weight-regular subtitle-1">
                    <!-- {{ feature.text }} -->
                  </h4>
                  <v-btn
                  v-bind="size"
                  rounded
                  outlined
                  color="white"
                  class="mt-6"
                  @click="openWebsite(feature.link)"
              >
                {{ feature.title }}
              </v-btn>
                </v-card>
              </v-hover>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<script>
export default {
  components: {
  },
  data() {
    return {
      dialog: false,
      videoId: "i8IvvHJssWE",
      features: [
        {
          img: require("@/assets/img/ethereum.png"),
          title: "Ethereum",
          // text: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
          link: "https://ethereum.org/en/"
        },
        // {
        //   img: require("@/assets/img/osmo.png"),
        //   title: "Osmosis",
        //   // text: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        //   link: "https://osmosis.zone/"
        // },
        {
          img: require("@/assets/img/evmos.png"),
          title: "Evmos",
          // text: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
          link: "https://evmos.org/"
        },
      ],
    };
  },
  watch: {
    dialog(value) {
      if (!value) {
        this.pause();
      }
    },
  },
  methods: {
    openWebsite(content) {
      window.open(content, '_blank');
    },
    ready(event) {
      this.player = event.target;
    },
    playing(event) {
      // The player is playing a video.
    },
    change() {
      // when you change the value, the player will also change.
      // If you would like to change `playerVars`, please change it before you change `videoId`.
      // If `playerVars.autoplay` is 1, `loadVideoById` will be called.
      // If `playerVars.autoplay` is 0, `cueVideoById` will be called.
      this.videoId = "another video id";
    },
    stop() {
      this.player.stopVideo();
    },
    pause() {
      this.player.pauseVideo();
    },
  },
};
</script>

<style lang="scss">
.circle {
  stroke: white;
  stroke-dasharray: 650;
  stroke-dashoffset: 650;
  -webkit-transition: all 0.5s ease-in-out;
  opacity: 0.3;
}
.playBut {
  /*  border: 1px solid red;*/
  display: inline-block;
  -webkit-transition: all 0.5s ease;
  .triangle {
    -webkit-transition: all 0.7s ease-in-out;
    stroke-dasharray: 240;
    stroke-dashoffset: 480;
    stroke: white;
    transform: translateY(0);
  }
  &:hover {
    .triangle {
      stroke-dashoffset: 0;
      opacity: 1;
      stroke: white;
      animation: nudge 0.1s ease-in-out;
      @keyframes nudge {
        0% {
          transform: translateX(0);
        }
        30% {
          transform: translateX(-5px);
        }
        50% {
          transform: translateX(5px);
        }
        70% {
          transform: translateX(-2px);
        }
        100% {
          transform: translateX(0);
        }
      }
    }
    .circle {
      stroke-dashoffset: 0;
      opacity: 1;
    }
  }
}
.btn-play {
  transition: 0.1s;
}
.svg-border-waves .v-image {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3rem;
  width: 100%;
  overflow: hidden;
}
#hero {
  z-index: 0;
}
.svg-border-waves img {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  margin-bottom: -2px;
  z-index: -1;
}
.cardColor {
   background-color: rgba(0, 0, 0, 1) !important;
   border-color: white !important;
 }
.card {
  min-height: 30px;
  padding: 10px;
  transition: 0.5s ease-out;
}
.card .v-image {
  margin-bottom: 15px;
  transition: 0.75s;
}
.card h1 {
  margin-bottom: 10px;
}
.zoom-efect {
  transform: scale(1.1);
}
.up {
  transform: translateY(-20px);
  transition: 0.5s ease-out;
}
section {
  position: relative;
}
</style>