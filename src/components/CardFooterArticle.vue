<template>
  <div>
    <div class="title">{{ name }}</div>
  </div>
</template>

<script>
export default {
  name: 'CardFooterArticle',
  props: {
    name: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
  .card-footer-article {
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

      @keyframes show {
        from {
          opacity: 0;
        }
        to {
          opacity: 1;
        }
      }

      &.ease-in {
        text-overflow: unset;
        white-space: normal;
        animation: show 0.35s ease-in 0s;
      }
    }
  }
</style>
