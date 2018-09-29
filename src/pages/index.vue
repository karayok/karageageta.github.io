<template>
  <section class="main">
    <card
      v-for="item in appList"
      :key="item.name"
      :name="item.name"
      :url="item.url"
      :isApp="true"
      :description="item.description"
      :image="item.image"
      :isAndroid="item.is_android"
      :isIos="item.is_ios"
    />
    <h2 class="heading">ARTICLES</h2>
    <card
      v-for="item in feeds"
      :key="item.title[0]"
      :name="item.title[0]"
      :isApp="false"
      :url="item.link[0].$.href"
      :image="item.link[1].$.href"
    />
  </section>
</template>

<script>
import axios from 'axios'
import xml2js from 'xml2js'
import Card from '~/components/Card.vue'
import AppList from '~/static/data/appList.json'

export default {
  components: {
    Card
  },
  data () {
    axios.get('https://karage-ageta.hatenablog.com/feed')
      .then(response => {
        const self = this
        xml2js.parseString(response.data, function (err, result) {
          // TODO : fix
          if (err) {
            console.log(err)
          }
          self.feeds = typeof result.feed.entry !== 'undefined' ? result.feed.entry.slice(0, 6) : {}
        })
      })
    return {
      feeds: this.feeds,
      appList: AppList.apps
    }
  }
}
</script>

<style lang="scss">
  .heading {
    font-family: $heading-font-family !important;
    font-weight: normal;
    padding: $spacing-xxx-small 0;
    letter-spacing: $spacing-xxx-small;
    border-bottom: $primary-text-color 1px solid;
  }
</style>
