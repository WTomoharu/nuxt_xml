<template>
  <v-layout>
    <v-flex class="text-center">
      <h1>Welcome, This is {{ title }} Page</h1>
      <h1>Status: {{ status }}</h1>
      <h2>{{ RssR }}</h2>
    </v-flex>
  </v-layout>
</template>

<script>
// const doc = new jsdom.JSDOM(xml)
// return { RssR: doc, xml }

import axios from 'axios'

export default {
  data () {
    return {
      title: 'Home'
    }
  },
  asyncData ({ params }) {
    return axios.get('https://note.com/notemag/rss').then((res) => {
      const xml = res.data
      return { RssR: xml, status: '正常にRSSを取得' }
    }).catch(async () => {
      try {
        const ofJSON = await import('~/static/xml_data.js').then((res) => { return res })
        return { RssR: ofJSON.xml, status: 'オフラインXMLを取得' }
      } catch (err) {
        return { RssR: Object.keys(err), status: 'XMLの取得を失敗' }
      }
    })
  }
}
</script>
