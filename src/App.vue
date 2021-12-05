<template>
  <div id="app">
    <header id="nav">
      <tr style="text-align: center;">
        <th class="navItem" @click="goTo('Home')">
          <a id="Home" href="#home">
            <h4 id="b" v-if="isAt == 'Home'" style="color: rgb(255, 165, 0);">Home</h4>
            <h4 v-else id="a">Home</h4>
          </a>
        </th>
        <th class="navItem" @click="goTo('About')">
          <a id="About" href="#about">
            <h4 id="b" v-if="isAt == 'About'" style="color: rgb(255, 165, 0);">About</h4>
            <h4 v-else id="a">About</h4>
          </a>
        </th>
        <th class="navItem" @click="goTo('Experience')">
          <a id="Experience" href="#experience">
            <h4 id="b" v-if="isAt == 'Experience'" style="color: rgb(255, 165, 0);">Experience</h4>
            <h4 v-else id="a">Experience</h4>
          </a>
        </th>
        <th class="navItem" @click="goTo('Contact')">
          <h4 id="b" v-if="isAt == 'Contact'" style="color: rgb(255, 165, 0);">Contact</h4>
          <h4 v-else id="a">Contact</h4>
        </th>
      </tr>
    </header>
    <body style="margin: 0;">
      <router-view/>
    </body>
    <div class="goUp" @click="goUp()" v-if="isAt != 'Contact' && !isTop">
      <i class="fas fa-arrow-up"></i>
    </div>
    <div class="goDown" @click="goDown()" v-if="isAt != 'Contact' && isAt != 'Experience'">
      <i class="fas fa-arrow-down"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      isAt: "Home",
      isTop: true,
    }
  },
  watch: {
    $route (to, from) {
      if (to.path == "/Contact")
        this.isAt = "Contact";
      if (from.path == "/Contact" && to.path == '/') {
        this.isAt = "Home";
      }
    }
  },
  created () {
    window.addEventListener('scroll', this.handleScroll);
  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll);
  },
  mounted() {
    this.isTop = window.scrollY == 0 ? true : false;
  },
  methods: {
    handleScroll (event) {
      if (this.$router.currentRoute.path == '/Contact')
        return;
      var tmp = window.screen.availHeight;
      var actS = window.scrollY;
      this.isTop = actS == 0 ? true : false;
      if (actS >= 0 && actS < tmp * 0.75)
        this.isAt = "Home";
      else if (actS >= tmp * 0.8 && actS < tmp * 1.5)
        this.isAt = "About";
      else if (actS >= tmp *1.5)
        this.isAt = "Experience";
    },
    goTo(path) {
      if (path == "Contact" && this.$router.currentRoute.path != "/Contact")
        this.$router.push(path);
      else if (path != "Contact" && this.$router.currentRoute.path != "/")
        this.$router.push('/');
    },
    goUp() {
      window.scroll(0, 0);
      if (this.$router.currentRoute.hash[0] == '#' || this.$router.currentRoute.path != '/')
        this.$router.push('/');
    },
    goDown() {
      if (this.isAt == 'Home')
        document.getElementById("About").click();
      else if (this.isAt == "About")
        document.getElementById("Experience").click();
    }
  }
}
</script>

<style>
#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  background: linear-gradient(338deg, #a1c4fd, #667eea, #764ba2);
  background-size: 100% 100%;
}

#nav {
  border-bottom: 1px solid #AFAFAF;
  position: fixed;
  right: 0;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;

  background: rgb(255,255,255);
  background: linear-gradient(90deg, rgba(255,255,255,0.10407913165266103) 0%, rgba(255,255,255,0.35) 50%, rgba(255,255,255,0.1) 100%);
}

.navItem {
  padding-left: 15px;
}

#b:hover {
  cursor: pointer;
  color: #ffa500;
}

#a:hover {
  cursor: pointer;
  animation: hoverColor 0.4s;
  color: #ffa500;
}
@keyframes hoverColor {
  from{color: #2c3e50;}
  to{color: #ffa500;}
}

html {
  scroll-behavior: smooth;
}

a {
  text-decoration: none;
  color: #2c3e50;
}

.goUp {
  width: 30px;
  height: 30px;
  border: 1px solid white;
  border-radius: 100%;
  background-color: #C9C5C5D7;
  cursor: pointer;
  position: fixed;
  right: 10px;
  bottom: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.goDown {
  cursor: pointer;
  position: fixed;
  left: 10px;
  margin-bottom: 10px;
  width: 30px;
  height: 30px;
  border: 1px solid white;
  border-radius: 100%;
  background-color: #C9C5C5D7;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* #nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
} */
</style>
