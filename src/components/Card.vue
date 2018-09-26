<template>
  <vs-col
    class="card"
    vs-type="flex"
    vs-justify="center"
    vs-align="center"
    vs-w="3"
  >
    <a
      class="card-container"
      :href="url"
      target="_blank"
      rel="noopener"
      v-on:mouseover="showDescription"
      v-on:mouseout="disableDescription"
    >
      <img :src="image" />
      <card-footer-app
        class="card-footer-app"
        v-show="isApp"
        :name="name"
        :description="description"
        :isAndroid="isAndroid"
        :isIos="isIos"
      />
      <card-footer-article
        class="card-footer-article"
        v-show="!isApp"
        :name="name"
      />
    </a>
  </vs-col>
</template>

<script>
import CardFooterApp from '~/components/CardFooterApp.vue'
import CardFooterArticle from '~/components/CardFooterArticle.vue'

export default {
  name: 'Card',
  components: {
    CardFooterApp,
    CardFooterArticle
  },
  props: {
    name: {
      type: String,
      required: true
    },
    url: {
      type: String,
      required: true
    },
    isApp: {
      type: Boolean,
      required: true
    },
    description: {
      type: String,
      required: false,
      default: ''
    },
    image: {
      type: String,
      required: false
    },
    isAndroid: {
      type: Boolean,
      required: false,
      default: false
    },
    isIos: {
      type: Boolean,
      required: false,
      default: false
    },
    isWeb: {
      type: Boolean,
      required: false,
      default: false
    },
    isDesktop: {
      type: Boolean,
      required: false,
      default: false
    }
  },
  methods: {
    showDescription () {
      const selector = this.isApp ? '.card-footer-app' : '.card-footer-article'
      const footer = event.currentTarget.querySelector(selector)
      footer.classList.remove('ease-out')
      footer.classList.add('ease-in')
      if (this.isApp) {
        footer.querySelector('.description').classList.add('ease-in')
      } else {
        footer.querySelector('.title').classList.add('ease-in')
      }
    },
    disableDescription () {
      const selector = this.isApp ? '.card-footer-app' : '.card-footer-article'
      const footer = event.currentTarget.querySelector(selector)
      footer.classList.remove('ease-in')
      footer.classList.add('ease-out')
      if (this.isApp) {
        footer.querySelector('.description').classList.remove('ease-in')
      } else {
        footer.querySelector('.title').classList.remove('ease-in')
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  .card {
    margin: $spacing-small;
    min-width: 176px;
    position: relative;
    border-radius: 8px;
    background: $light-background;
    box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
    transition: all 0.3s cubic-bezier(.25,.8,.25,1);

    &:hover {
      top: -8px;
      box-shadow:rgba(0, 0, 0, 0.3) 0 16px 16px 0;
      -webkit-box-shadow:rgba(0, 0, 0, 0.3) 0 16px 16px 0;
      -moz-box-shadow:rgba(0, 0, 0, 0.3) 0 16px 16px 0;
    }

    &::before {
      display: block;
      content: '';
      padding-top: 100%;
    }

    a {
      color: $primary-text-color;
    }

    .card-container {
      position: absolute;
      top: 0;
      width: 100%;
      height: 100%;
      box-sizing: border-box;
      border-radius: 8px;

      img {
        width: 100%;
        height: 100%;
        border-radius: 8px;
        object-fit: cover;
        object-position: 50% 0;
        top: 0;
      }
    }
  }
</style>
