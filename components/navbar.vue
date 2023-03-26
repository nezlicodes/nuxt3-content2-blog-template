<template>
  <div>
    <nav>
      <div>
      </div>
      <ul class="nav w-full flex justify-between items-center sm-hidden">
        <li class="flex-1">
          <nuxt-link class="nav-link" to="/"> Home</nuxt-link>
        </li>
       

       <div class="flex items-center gap-5">
         <a class="nav-link" href="https://github.com/nezlicodes" target="_blank">  <Icon name="fa6-brands:github"></Icon></a>
         <a class="nav-link"  href="https://twitter.com/Jamstacklily"  target="_blank">  <Icon name="fa6-brands:twitter"></Icon></a>
         <a class="nav-link"  href="mailto:contact@lylianezli.com"  target="_blank">  <Icon name="fa6-solid:envelope"></Icon></a>
       </div>
      </ul>

      <div class="full-w mobile-nav md-hidden">
        <button class="toggle-button" @click="handleMenu">
          <font-awesome-icon
            size="lg"
            :icon="['fas', openMenu ? 'times' : 'bars']"
          />
        </button>

        <ul
          @mouseleave="closeMenu"
          v-if="openMenu"
          :class="openMenu ? 'mobile-list-active' : 'mobile-list-hidden'"
        >
          <li @click="closeMenu">
            <nuxt-link class="nav-link" to="/">Home</nuxt-link>
          </li>
          <li @click="closeMenu">
            <nuxt-link class="nav-link" to="/blog">Blog</nuxt-link>
          </li>
          
        </ul>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      openMenu: false,
    };
  },
  methods: {
    handleMenu() {
      this.openMenu = !this.openMenu;
    },
    closeMenu() {
      this.openMenu = false;
    },
  },
};
</script>

<style  scoped>
/* nav */
nav {
  height: 60px;
  padding: 10px;
  box-shadow: 0px 0px 7px 8px rgba(0, 0, 0, 0.2);
  display: flex;
  background-color: var(--primary-color);
}

ul {
  align-items: center;
}

ul li:hover {
  animation: scale ease-in-out 500ms 2 alternate;
  text-decoration: underline;
}

/* Full screen nav */
ul.nav {
  display: flex;
  gap: 20px;
  justify-self: center;
  justify-items: center;
}

/* mobile nav */
.mobile-nav {
  justify-content: end;
}

ul.mobile-list-hidden {
  width: 0px;
  height: 0px;
  right: 20px;
  background-color: transparent;
  transition: background-color 550ms ease-in;
}

ul.mobile-list-active {
  width: 100vw;
  position: absolute;
  top: 40px;
  right: 0;
  top: 0;
  padding: 40px 0;
  background-color: var(--secondary-color);
  font-size: 30px;
  display: grid;
  justify-content: center;
  box-shadow: 0px 0px 7px 8px rgba(0, 0, 0, 0.2);
}

button.toggle-button {
  z-index: 2;
  margin-top: 5px;
  margin-right: 10px;
  color: var(--primary-color);
}

@keyframes scale {
  0% {
    transform: translateX(-3px);
  }
  100% {
    transform:translateX(3px);
  }
}

/* Positionning */
.inline {
  justify-content: space-between;
}

.jc-end {
  width: 124px;
}

.jc-center {
  display: flex;
  justify-self: center;
  justify-items: center;
  justify-content: center;
}

/* Links */

.nav-link {
  color: var(--secondary-color);
}

.nuxt-link-exact-active {
  color: white;
  font-size: 18px;
}

ul.mobile-list-active > li > .nuxt-link-exact-active {
  font-size: 30px;
}

.logo {
  position: absolute;
  width: 76px;
  display: inline-block !important;
  height: 72px;
  top: 10px;
}
</style>