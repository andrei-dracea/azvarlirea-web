<template>
  <nav
    class="navbar is-mobile is-fixed-top"
  >
    <div class="container is-fluid">
      <div class="navbar-brand">
        <a class="navbar-item" href="/">
          <img :src="logo" />
        </a>
      </div>

      <div class="navbar-menu">
        <transition name="fade">
          <div id="menu" v-if="mobileNavActive" class="has-text-centered">
            <div>
              <ul class="is-size-3">
                <!-- <li>
                    <router-link
                      :to="{ name: 'infomedic' }"
                      class="navbar-item"
                    >
                      Ai nevoie de echipament medical?
                    </router-link>
                  </li> -->
                <li>
                  <router-link :to="{ name: 'community' }" class="navbar-item">
                    Donatori
                  </router-link>
                </li>
                <li>
                  <router-link :to="{ name: 'helping' }" class="navbar-item">
                    Vrei să te implici?
                  </router-link>
                </li>
              </ul>
            </div>
          </div>
        </transition>
        <div class="navbar-end">
          <div class="navbar-item">
          </div>
          <div class="navbar-item">
            <a
              @click="toggleMobileNav"
              class="button is-primary is-outlined is-menu"
              :class="{ 'is-active': mobileNavActive }"
            >
              <span v-if="!mobileNavActive">MENIU</span>
              <b-icon v-else icon="times" />
            </a>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  props: {
    logo: {
      type: String,
      required: false,
    },
    sticky: {
      type: Boolean,
      required: false,
    },
  },
  data() {
    return {
      mobileNavActive: false,
    }
  },
  computed: {
    navLinks() {
      return this.$site.themeConfig.nav
    },
  },
  methods: {
    toggleMobileNav() {
      this.mobileNavActive = !this.mobileNavActive
    },
  },
}
</script>

<style scoped></style>
