<template>
  <section class="main">
    <vs-row
      vs-align="flex-end"
      vs-type="flex"
      vs-justify="flex-end"
      vs-w="12"
    >
      <vs-col
        class="heading"
        vs-type="flex"
        vs-justify="flex-start"
        vs-align="flex-start"
        vs-lg="10"
        vs-sm="11"
        vs-xs="11"
      >
        <h2>WORKS</h2>
      </vs-col>
    </vs-row>
    <vs-row
      vs-align="center"
      vs-type="flex"
      vs-justify="center"
      vs-w="12"
    >
      <vs-col
        vs-type="flex"
        vs-justify="center"
        vs-align="center"
        vs-lg="8"
        vs-sm="11"
        vs-xs="11"
      >
        <vs-row
          vs-align="center"
          vs-type="flex"
          vs-justify="space-between"
          vs-w="12"
        >
          <app-card
            v-for="item in appList"
            :key="item.name"
            :name="item.name"
            :image="item.image"
            :url="item.url"
            :isAndroid="item.is_android"
            :isIos="item.is_ios"
          />
        </vs-row>
      </vs-col>
    </vs-row>
  </section>
</template>

<script>
import AppCard from '~/components/AppCard.vue'
import AppList from '~/static/data/appList.json'

export default {
  components: {
    AppCard
  },
  data () {
    return {
      appList: AppList.apps
    }
  }
}
</script>

<style lang="scss">
  .heading {
    padding: 4px 0;
    border-bottom: rgba(7, 33, 42, 1) 1px solid;
  }
</style>
