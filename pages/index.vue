<template>
  <div class="background" style="font-family: 'Open Sans', sans-serif">
    <!-- Block1 takes 100vh and 100vw -->
    <div class="block1">
      <v-row class="pa-0 ma-0 rowblock1" justify="center" align="center">
        <v-spacer></v-spacer>
        <v-col
          justify="center"
          align="center"
          cols="12"
          xs="12"
          sm="12"
          md="auto"
        >
          <v-avatar
            style="
              margin-bottom: -60px;
              z-index: 2;
              box-shadow: 0 5px 10px 0 rgba(23, 24, 25, 0.6);
            "
            size="150"
          >
            <v-img src="profile/profile.png" alt="Matias Fanger" />
          </v-avatar>
          <!-- About me -->
          <v-card color="rgb(44, 64, 90, 0.0)" style="" outlined elevation="10">
            <v-card-text
              class="text-center pt-3 mt-16"
              style="font-size: 1.5rem; color: white"
            >
              <h2 style="letter-spacing: 3px; line-height: 1.6">
                Hello, Universe! I'm<span class="glowStar"> Matias.</span>
              </h2>
              <h5 class="mt-6">
                I am a Full Stack Web Developer based in <span class="light-blue--text">Arg</span><span class="white--text">ent</span><span class="light-blue--text">ina</span>
              </h5>
              <h5 class="mt-6">
                I love working with Nuxt, Vue, Vuetify, Tailwind, Python, Node, Firebase and much
                more! <v-icon color="blue">mdi-console-network</v-icon>
              </h5>
              <h5 class="mt-6">Send me a PM if you need some help.</h5>
            </v-card-text>
            <!-- Socials -->
            <v-card-actions class="justify-center">
              <v-btn
                href="https://www.linkedin.com/in/matifanger/" class="ma-1" text icon>
                <v-icon color="white" x-large>mdi-linkedin</v-icon></v-btn
                >
              <v-btn href="https://github.com/matifanger" class="ma-1" text icon
                ><v-icon color="white" x-large>mdi-github</v-icon></v-btn
              >
              <v-btn href="https://wa.link/aq1xfn" class="ma-1" text icon
                ><v-icon color="white" x-large>mdi-whatsapp</v-icon></v-btn
              >
              <v-btn href="mailto:matifanger@outlook.com" class="ma-1" text icon
                ><v-icon color="white" x-large>mdi-email</v-icon></v-btn
              >
            </v-card-actions>

            <div color="rgb(44, 64, 90, 0.5)">
              <v-btn
              class="mt-2"
                outlined
                href="https://drive.google.com/file/d/1WmrjHfjrHsh4f5yvJ_CR6JlFL-CmRG4I/view?usp=sharing"
                color="success"
                target="_blank"
                >Resume<v-icon right>mdi-file</v-icon></v-btn
              >
            </div>
          </v-card>
        </v-col>
        <v-spacer></v-spacer>
      </v-row>
    </div>
    <div class="block2">
      <v-row class="pa-0 ma-0 rowblock2" justify="center" align="center">
        <v-col md="10" class="d-flex justify-center">

          <v-slide-group active-class="success" show-arrows dark>
            <v-slide-item
              v-for="(project, index) in projects"
              :key="index"
              v-slot:default="{ active, toggle }"
            >
              <a :href="project.url">
                <v-hover v-slot:default="{ hover }">
                  <v-card
                    :elevation="hover ? 12 : 0"
                    :color="active ? undefined : 'grey lighten-5'"
                    class="mr-3 rounded-0"
                    :class="{ 'on-hover': hover }"
                    height="200"
                    width="350"
                    @click="toggle"
                  >
                    <v-card
                      width="100%"
                      style="position: absolute; z-index: 5; opacity: 0.6"
                      class="black darken-2 white--text"
                    >
                      <v-card-title height="10%" class="justify-center">{{
                        project.name
                      }}</v-card-title>
                    </v-card>
                    <v-img :src="project.image" aspect-ratio="1" height="200px">
                      <v-expand-transition>
                        <div
                          v-if="hover"
                          class="
                            d-flex
                            transition-fast-in-fast-out
                            black
                            darken-2
                            v-card--reveal
                            white--text
                          "
                          style="height: 40%"
                        >
                          <span class="ma-3" style="font-size: 20px">{{
                            project.description
                          }}</span>
                        </div>
                      </v-expand-transition>
                      <template v-slot:placeholder>
                        <v-row
                          class="fill-height ma-0"
                          align="center"
                          justify="center"
                        >
                          <v-progress-circular
                            indeterminate
                            color="black lighten-5"
                          ></v-progress-circular>
                        </v-row>
                      </template>
                    </v-img>
                  </v-card>
                </v-hover>
              </a>
            </v-slide-item>
          </v-slide-group>
        </v-col>
      </v-row>
    </div>

    <v-footer absolute color="rgb(255, 255, 255, 0.1)" height="58">
      <v-row>
        <v-col align="center">
          <span class="white--text"
            ><v-btn
              color="white"
              text
              small
              href="https://www.linkedin.com/in/matifanger/"
              >Designed by Matias Fanger</v-btn
            >
            &copy; {{ new Date().getFullYear() }}</span
          >
        </v-col>
      </v-row>
    </v-footer>
  </div>
</template>

<script>
export default {
  head() {
    const title = "";
    return { title };
  },
  data() {
    return {
      projects: [
        {
          name: "Vaccine World Tracker",
          url: "https://vaccine-world-tracker.netlify.app/",
          description: "Vaccine's information around the World!",
          stack: ['vue', 'vuetify', 'nuxt', 'node', 'netlify', 'api' ],
          image: "https://i.gyazo.com/af1bddfd8dd9672345c61fb6eab5853a.png",
          github: "https://github.com/matifanger/vaccine-world-tracker",
        },
        {
          name: "Axie Partners",
          url: "https://axie.partners",
          description: "Hire or get hired in Axie Infinity!",
          stack: ['vue', 'vuetify', 'nuxt', 'node' ],
          image: "https://i.gyazo.com/c501cadf0412e81ebbc51f258470751e.jpg",
          github: "https://github.com/matifanger/axie-partners",
        },
        {
          name: "Protected Bookmarks",
          url: "https://protected-bookmarks.netlify.app/",
          description: "Save your bookmarks in the cloud!",
          stack: ['vue', 'tailwind', 'nuxt', 'node', 'firebase', 'netlify' ],
          image: "https://i.gyazo.com/0794beaeb2eee369047f137fbbc4a7ce.png",
          github: "https://github.com/matifanger/protected-bookmarks-v2",
        },
        {
          name: "SLP graph price",
          url: "https://slp-price.netlify.app/",
          description: "Simple SLP price graph.",
          stack: ['vue', 'vuetify', 'nuxt', 'node', 'firebase', 'api'],
          image: "https://i.gyazo.com/43c8a4dbce01548e3db7bddc97db3830.png",
          github: "https://github.com/matifanger/slp-price",
        },
        {
          name: "CSGO CONFIG MANAGER",
          url: "https://csgo-config-manager.netlify.app/",
          description: "Optimize your config to maximize your FPS in CSGO",
          stack: ['vue', 'Tailwind CSS', 'nuxt'],
          image: "https://github.com/matifanger/csgo-config-manager/raw/master/.github/main.png",
          github: "https://github.com/matifanger/csgo-config-manager",
        },
        {
          name: "Free Proxy",
          url: "https://master.d3r5rgkuxurm4k.amplifyapp.com",
          description: "You can get some free proxies right here.",
          stack: ['vue', 'vuetify', 'nuxt', 'node', 'firebase', 'netlify'],
          image: "https://i.gyazo.com/72c2cae932ae2ea057cbe6bcbddc5cf7.png",
          github: "https://github.com/matifanger/freeproxy",
        },
        {
          name: "IP Logger",
          url: "https://lcloud-support.netlify.app/",
          description: "Obtain system and location information.",
          stack: ['vue', 'vuetify', 'nuxt', 'node', 'firebase', 'netlify'],
          image: "https://i.gyazo.com/404fb79c7930d1a8287ecc89277a4f3e.png",
          github: "https://github.com/matifanger/ip-logger",
        },
        {
          name: "WZ-Statistics",
          url: "https://wz-statistics.herokuapp.com",
          description: "See your stats in COD Warzone and calculate your next kd",
          stack: ['vue', 'vuetify', 'nuxt', 'node', 'heroku'],
          image: "https://i.gyazo.com/00a1f17ec85020f03a1d7b90d7900e0f.png",
          github: "https://github.com/matifanger/WZ-Statistics",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@600&display=swap");

.background {
  background-image: linear-gradient(transparent, black 20%),
    url("/universe.jpg");

  height: 200%;
  width: 100%;

  // background-position: center;
  // position: absolute;
  // background-size: 100%; /* Make sure you call background-size after the background. */
  // background-attachment: fixed;
}

.block1 {
  width: 100vw;
  height: 100vh;
}

.rowblock1 {
  width: 100vw;
  height: 100vh;
}

.block2 {
  background-color: black;
  background-image: linear-gradient(to top, transparent, black 40%),
    url("/universe.jpg");

  width: 100vw;
  height: 60vh;
}

.rowblock2 {
  width: 100vw;
  height: 60vh;
}

.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: 0.5;
  position: absolute;
  width: 100%;
}

.glowStar {
  background-image: url("~/static/gifs/sparkles.gif");
  background-position: 50% 50%;
  background-repeat: repeat;
  color: rgb(255, 255, 255);
}
</style>