<template>
  <div class="background" style="font-family: 'Open Sans', sans-serif">
    <div class="block1">
          <v-card class="content" color="rgb(44, 64, 90, 0.0)" outlined elevation="10">
            <v-card-text
              class="text-center"
              style="font-size: 1.5rem; color: white"
            >
              <h2 style="letter-spacing: 3px; line-height: 1.6">
                Oops! something happened. <v-icon color="grey" large>mdi-emoticon-sad-outline</v-icon>

                <h6 v-if="error.statusCode === 404">Error: {{ pageNotFound }}</h6>
                <h6 v-else>{{ otherError }}</h6>
              </h2>
    <img width="350" height="" src="/404.png">
      <div class="mt-5"><NuxtLink to="/" style="text-decoration: none;">
      <span class="glowStar">Bring me back! <v-icon color="blue">mdi-keyboard-return</v-icon></span>
    </NuxtLink></div>
            </v-card-text>
          </v-card>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  data () {
    return {
      pageNotFound: '404 Not Found',
      otherError: 'An error occurred'
    }
  },
  head () {
    const title = this.error.statusCode === 404 ? this.pageNotFound+' - ' : this.otherError+' - '
    return { title }
  }
}
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@600&display=swap");

h1 {
  font-size: 20px;
}

.background {
  background-image: linear-gradient(transparent, black 20%),
    url("/universe.jpg");

  height: 200%;
  width: 100%;
}

.block1 {
  width: 100vw;
  height: 100vh;
}

.content {
    position: absolute;
  left: 50%;
  top: 50%;
  -webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}

.glowStar {
  background-image: url("~/static/gifs/sparkles.gif");
  background-position: 50% 50%;
  background-repeat: repeat;
  color: rgb(255, 255, 255);
}
</style>
