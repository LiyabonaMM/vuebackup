<template>
  <header class="page-header">
    <!-- Background -->
    <div class="content-top-bg">
      <div class="content-top-bg-overlay"></div>
    </div>

    <!-- Container -->
    <div class="container">
      <div class="container-content-wrapper">
        <img :src="headerData.srcImage" class="img-fluid" />
        <h1 class="heading mt-4">{{ headerData.title }}</h1>
        <p class="subheading">{{ headerData.subtitle }}</p>
        <XLButton
          :icon="headerData.button.icon"
          :label="headerData.button.label"
          @click="_onButtonClicked()"
        ></XLButton>
      </div>
    </div>
  </header>
</template>

<script setup>
import agencyData from '../data/db.json'
import XLButton from "../components/XLButton.vue"
import {useLayout} from '../composables/layout.js'

const headerData = agencyData.header

const _onButtonClicked = () => {
  useLayout().scrollToSection(headerData.button.targetSection);
}
</script>

<style scoped lang="scss">
@import "../scss/_theming.scss";

.page-header {
  min-height: 800px;
  position: relative;
}

.content-top-bg {
  background-image: url('https://i.postimg.cc/158Cywh4/background-image2-jpg-min.png');
  background-position: center;
  background-size: cover;
  height: 100%;
  position: absolute;
  width: 100%;
  z-index: -1;
}

.container {
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  width: 100%;
  color: $white;
  padding-left: 1rem;
  padding-right: 1rem;

  img {
    max-height: 40vh;
    margin-top: 8rem;
    max-width: 70vw;
  }

  .heading {
    font-size: 2rem;
    font-weight: 700;
    text-transform: uppercase;
    font-family: $headings-font-family;
  }

  .subheading {
    font-size: 1rem;
    color: $white-faded;
    font-family: $subheadings-font-family;
  }
}

@include media-breakpoint-up(lg) {
  .page-header {
    height: 100vh;
    position: relative;
  }

  .container {
    .heading {
      font-size: 4rem;
      line-height: 5.25rem;
    }

    .subheading {
      font-size: 1.7rem;
    }

    img {
      margin-top: 2rem;
    }
  }
}
</style>
