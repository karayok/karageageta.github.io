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
        <div class="description">{{ description }}</div>
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
      const footer = event.currentTarget.querySelector('.card-footer')
      footer.classList.remove('ease-out')
      footer.classList.add('ease-in')
      const description = footer.querySelector('.description')
      description.classList.add('ease-in')
    },
    disableDescription () {
      const footer = event.currentTarget.querySelector('.card-footer')
      footer.classList.remove('ease-in')
      footer.classList.add('ease-out')
      const description = footer.querySelector('.description')
      description.classList.remove('ease-in')
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
    background: $primaryColor;
    box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
    transition: all 0.3s cubic-bezier(.25,.8,.25,1);

    &:hover {
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
      color: $primaryTextColor;
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
        background: linear-gradient(315deg, rgba(255, 255, 255, 0.6) 0%, rgba(255, 255, 255, 0.9) 100%);
        position: absolute;
        bottom: 0;
        width: 100%;
        height: 20%;
        max-height: 20%;
        min-height: 48px;
        border-radius: 0 0 8px 8px;

        &.ease-in {
          height: 50%;
          max-height: 50%;
          transition: max-height 0.2s ease-in;
        }

        &.ease-out {
          height: 20%;
          max-height: 20%;
          transition: 0.2s ease-in;
        }

        .title {
          font-weight: bold;
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
        }

        .description {
          margin-top: 8px;
          color: $secondaryTextColor;
          display: none;

          @keyframes show {
            from {
              opacity: 0;
            }
            to {
              opacity: 1;
            }
          }

          &.ease-in {
            display: block;
            animation: show 0.35s ease-in 0s;
          }
        }

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
