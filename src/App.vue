<template>
  <div id="app">
    <LeftNavBar v-if="page !== 0"
                :numPages="numPages"
                :page="page"
                :navigate="navigate"
                :pageTitle="pageTitle"
                :busy="assessing" />
    <router-view></router-view>
    <RightNavBar :numPages="numPages"
                 :page="page"
                 :navigate="navigate"
                 :busy="assessing" />
  </div>
</template>

<script>
import RightNavBar from '@/components/RightNavBar'
import LeftNavBar from '@/components/LeftNavBar'

export default {
  name: 'app',
  components: {
    RightNavBar,
    LeftNavBar
  },
  data() {
    return {
      numPages: 5,
      page: 0,
      pageTitle: 'page',
      assessing: false,
    }
  },
  methods: {
    navigate: function(id) {
      if(this.page == id) return;
      switch(id) {
        case 0:
          this.$router.push("/");
          break;
        case 1:
          this.$router.push("/tutorial");
          break;
        case 2:
          this.$router.push("/practice");
          break;
        case 3:
          this.$router.push("/assessment");
          break;
        case 4:
          this.$router.push("/assessment/results");
          break;
        default:
          console.error("Error Navigating: Index doesn't exist!");
          this.$router.push("/");
          break;
      }
      this.page = id;
    }
  },
  watch: {
    $route: {
      immediate: true,
      handler(to) {
        this.page = parseInt(to.name);
        this.pageTitle = to.matched[0].props.default.title;

        if(this.pageTitle === 'titles.empty') this.assessing = true;
        else this.assessing = false;
      }
    }
  },
}
</script>

<style>
@font-face {
  font-family: "Avenir Next Bold";
  src: url("./assets/font/AvenirNext-Bold-01.ttf") format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: "Avenir Next Bold Italic";
  src: url("./assets/font/AvenirNext-BoldItalic-02.ttf") format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: "Avenir Next DemiBold";
  src: url("./assets/font/AvenirNext-DemiBold-03.ttf") format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: "Avenir Next DemiBold Italic";
  src: url("./assets/font/AvenirNext-DemiBoldItalic-04.ttf") format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: "Avenir Next Italic";
  src: url("./assets/font/AvenirNext-Italic-05.ttf") format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: "Avenir Next Medium";
  src: url("./assets/font/AvenirNext-Medium-06.ttf") format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: "Avenir Next Medium Italic";
  src: url("./assets/font/AvenirNext-MediumItalic-07.ttf") format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: "Avenir Next";
  src: url("./assets/font/AvenirNext-Regular-08.ttf") format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: "Avenir Next Heavy";
  src: url("./assets/font/AvenirNext-Heavy-09.ttf") format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: "Avenir Next Heavy Italic";
  src: url("./assets/font/AvenirNext-HeavyItalic-10.ttf") format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: "Avenir Next Ultralight";
  src: url("./assets/font/AvenirNext-UltraLight-11.ttf") format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: "Avenir Next Ultralight Italic";
  src: url("./assets/font/AvenirNext-UltraLightItalic-12.ttf") format('truetype');
  font-weight: normal;
}

#app {
  font-family: 'Avenir Next', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  height: 95vh;
  user-select: none;
  -webkit-tap-highlight-color: transparent;

}

html {
  font-size: 14px;
}

@media only screen and (max-width: 1100px) {
  html {
    font-size: 13px;
  }
}
@media only screen and (max-height: 500px) {
  html {
    font-size: 11px;
  }
}
@media only screen and (max-width: 900px) {
  html {
    font-size: 11px;
  }
}
@media only screen and (max-width: 750px) {
  html {
    font-size: 9px;
  }
}


@media only screen and (min-width: 1300px) {
  html {
    font-size: 16px;
  }
}
@media only screen and (min-width: 1500px) {
  html {
    font-size: 20px;
  }
}
@media only screen and (min-width: 2000px) {
  html {
    font-size: 26px;
  }
}
@media only screen and (min-width: 3000px) {
  html {
    font-size: 36px;
  }
}
@media only screen and (min-width: 4000px) {
  html {
    font-size: 50px;
  }
}
</style>
