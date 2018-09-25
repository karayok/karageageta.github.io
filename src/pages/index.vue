<template>
  <section class="main">
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
        </vs-row>
      </vs-col>
    </vs-row>
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
        <h2>ARTICLES</h2>
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
          <card
            v-for="item in feeds"
            :key="item.title[0]"
            :name="item.title[0]"
            :isApp="false"
            :url="item.link[0].$.href"
            :image="item.link[1].$.href"
          />
        </vs-row>
      </vs-col>
    </vs-row>
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
    padding: 4px 0;
    border-bottom: $primaryTextColor 1px solid;
  }
</style>
