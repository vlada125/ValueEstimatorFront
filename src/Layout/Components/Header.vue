<template>
  <div :class="headerbg" class="app-header header-shadow">
    <!-- <div class="logo-src" /> -->
    <div class="app-header__content">
      <div class="app-header-left">
        <!-- <MegaMenu /> -->
      </div>
      <div class="app-header-right">
        <UserArea />
      </div>
    </div>
    <div class="app-header__mobile-menu">
      <div>
        <button type="button" class="hamburger close-sidebar-btn hamburger--elastic"
          v-bind:class="{ 'is-active' : isOpen }" @click="toggleMobile('closed-sidebar-open')">
          <span class="hamburger-box">
            <span class="hamburger-inner"></span>
          </span>
        </button>
      </div>
    </div>
    <div class="app-header__menu">
      <span>
        <b-button class="btn-icon btn-icon-only" variant="primary" size="sm"
          v-bind:class="{ 'active' : isOpenMobileMenu }" @click="toggleMobile2('header-menu-open')">
          <div class="btn-icon-wrapper">
            <font-awesome-icon icon="ellipsis-v" />
          </div>
        </b-button>
      </span>
    </div>
  </div>
</template>

<script>
import UserArea from "./Header/HeaderUserArea";
// import MegaMenu from "./Header/MegaMenu";


import { library } from "@fortawesome/fontawesome-svg-core";
import { faEllipsisV } from "@fortawesome/free-solid-svg-icons";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

library.add(faEllipsisV);
export default {
  name: "Header",
  components: {
    UserArea,
    // MegaMenu
    "font-awesome-icon": FontAwesomeIcon
  },

  data() {
    return {
      isOpen: false,
      isOpenMobileMenu: false
    };
  },
  props: {
    headerbg: String
  },
  methods: {
    toggleMobile(className) {
      const el = document.body;
      this.isOpen = !this.isOpen;

      if (this.isOpen) {
        el.classList.add(className);
      } else {
        el.classList.remove(className);
      }
    },

    toggleMobile2(className) {
      const el = document.body;
      this.isOpenMobileMenu = !this.isOpenMobileMenu;

      if (this.isOpenMobileMenu) {
        el.classList.add(className);
      } else {
        el.classList.remove(className);
      }
    }
  }
};
</script>
