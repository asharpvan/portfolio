<template>
  <div id="app">
      <nav id="nav">
        <div class="menu-icon">
          <img @click="toggleMenu" src='../src/assets/app/menu_related/menu-bars.png' alt="menu" width="25" height="25">
        </div>
        <div><router-link class="logo" to="/">asharpvan</router-link></div>
        <!-- asharpvan -->
        <div class="menu">
          <ul id="ul">
            <li><router-link to="/about" v-on:click.native="toggleMenu">About</router-link></li>
            <li><router-link to="/featured" v-on:click.native="toggleMenu">Featured</router-link></li>
            <li><router-link to="/portfolio" v-on:click.native="toggleMenu">Portfolio</router-link></li>
          </ul>
        </div>
      </nav>
      <main>
        <router-view></router-view>
      </main>
      <hr>
      <div id="footer">
          <p>Copyright © 2018 Pranav Sah. All rights reserved.</p>
      </div> 
  </div>
</template>

<script>
export default {
  name: 'app',
  /* Life Cycle Methods */
  beforeCreate: function () {
    console.log('Before Create')
  },
  created: function () {
    console.log('Created')
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeMount: function () {
    console.log('Before Mount')
  },
  mounted: function () {
    console.log('Mounted')
  },
  beforeUpdate: function () {
    console.log('Before Update')
  },
  updated: function () {
    console.log('Updated')
  },
  beforeDestroy: function () {
    console.log('Before Destroy')
  },
  destroyed: function () {
    console.log('Destroyed')
    window.removeEventListener('scroll', this.handleScroll)
  },
  data () {
    return {
      msg: 'Welcome to Your Home Page'
    }
  },
  methods: {
    handleScroll: function (event) {
      console.log('Scrolled!!')
      if (window.scrollY > window.screenTop) {
        document.getElementById('nav').classList.add('black')
      } else {
        document.getElementById('nav').classList.remove('black')
      }
    },
    toggleMenu: function () {
      console.log('menu button clicked')
      // if (window.screen.width > 580) {
      // document.getElementById('ul').classList.toggle('showing')
      // }
      document.getElementById('ul').classList.toggle('showing')
    }
  }
}
</script>

<style>

.logo {
  font-weight: 900;
  position: fixed;
  float: left;
  margin: 16px 36px;
  color: #ffffff;
  font-weight: bolder;
  font-size: 24px;
  text-decoration: none;
}

nav {
  position: fixed;
  width: 100%;
  z-index: 100;
}

nav ul {
  list-style: none;
  background:  #000000;
  /* background:  rgba(0,0,0,0); */
  overflow: hidden;
  color: #ffffff;
  padding: 0;
  text-align: right;
  margin: 0;
  transition: 1s; 
}

nav.black ul {
  background:  #000000;
}

nav ul li {
  display: inline-block;
  padding: 18px; /* Controls nav bar height in Desktop */
  /* background-color: red; */
}

nav ul li a {
  text-decoration: none;
  color: #ffffff;
  font-size: 20px;
  /* background-color: aqua; */
}

.menu-icon {
  width: 100%;
  background: #000000;
  text-align: right;
  box-sizing: border-box;
  padding: 16px 24px;
  cursor: pointer;
  color: #ffffff;
  display: none;
}

@media (max-width: 580px) {
  .logo {
    position: fixed;
    top: 0;
    margin-top: 16px;
    margin-left: 16px;
  }
  nav ul {
    max-height: 0px;
    background: #000000;
  }
  nav.black ul {
    background: #000000;
  }
  .showing {
    max-height: 20em;
  }
  nav ul li {
    box-sizing: border-box;
    width: 100%;
    padding: 24px 0;
    text-align: center;
  }
  .menu-icon {
    display: block;
  }
}

@font-face {
  font-family: 'Quicksand';
  src: url('../src/assets/fonts/quicksand-regular-webfont.woff2') format('woff2'),
    url('../src/assets/fonts/quicksand-regular-webfont.woff') format('woff');
  font-weight: normal;
  font-style: normal;                
}

#app {
  font-family: Quicksand;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

body {
  margin: 0;
  padding: 0;
  /* overflow-y:hidden; */
}

#footer{
    display: table;
    text-align: center;
    margin: auto auto;
    font-size: 14px;
}
</style>
