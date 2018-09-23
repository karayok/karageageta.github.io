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
      <div class="card-footer">
        <div class="title">{{ name }}</div>
        <vs-row
          class="app-type-icons"
          vs-align="flex-end"
          vs-type="flex"
          vs-justify="flex-end"
          vs-w="8"
        >
          <vs-col v-if="isAndroid" vs-w="2">
            <img src="~/static/images/icons/ic_android.svg" />
          </vs-col>
          <vs-col v-if="isIos" vs-w="2">
            <img src="~/static/images/icons/ic_ios.svg" />
          </vs-col>
        </vs-row>
      </div>
    </a>
  </vs-col>
</template>

<script>
export default {
  name: 'AppCard',
  props: {
    name: {
      type: String,
      required: true
    },
    url: {
      type: String,
      required: true
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
      const footer = event.currentTarget.querySelector('.card-footer')
      footer.style.height = '50%'
      footer.style.maxHeight = '50%'
      footer.style.transition = 'max-height 0.25s ease-in'
    },
    disableDescription () {
      const footer = event.currentTarget.querySelector('.card-footer')
      footer.style.height = '20%'
      footer.style.maxHeight = '20%'
      footer.style.transition = '0.25s ease-in'
    }
  }
}
</script>

<style lang="scss" scoped>
  .card {
    margin: 24px;
    min-width: 176px;
    position: relative;
    border-radius: 8px;
    background: rgba(14, 70, 90, 0.9);
    box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
    transition: all 0.3s cubic-bezier(.25,.8,.25,1);

    &:hover {
      box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
    }

    &::before {
      display: block;
      content: '';
      padding-top: 100%;
    }

    a {
      color: rgb(38, 50, 56);
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
        object-position: 0 0;
        top: 0;
      }

      .card-footer {
        padding: 4px;
        background: rgba(255, 255, 255, 0.9);
        position: absolute;
        bottom: 0;
        width: 100%;
        height: 20%;
        max-height: 20%;
        min-height: 48px;

        .app-type-icons {
          position: absolute;
          right: 4px;
          bottom: 4px;
          img {
            height: 20px;
            width: auto;
          }
        }
      }
    }
  }
</style>
