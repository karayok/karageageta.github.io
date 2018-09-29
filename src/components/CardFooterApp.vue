<template>
  <div>
    <div class="title">{{ name }}</div>
    <div class="description">{{ description }}</div>
    <div class="app-type-icons">
      <img v-if="isAndroid" src="~/static/images/icons/ic_android.svg" />
      <img v-if="isIos" src="~/static/images/icons/ic_ios.svg" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardFooterApp',
  props: {
    name: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: false,
      default: ''
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
  }
}
</script>

<style lang="scss" scoped>
  .card-footer-app {
    padding: $spacing-xx-small;
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
      margin-top: $spacing-xx-small;
      color: $secondary-text-color;
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
      right: 0;
      bottom: 0;
      img {
        height: 20px;
        width: auto;
      }
    }
  }
</style>
