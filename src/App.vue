<template>
  <div id="app">
     <router-view></router-view>
  </div>
</template>

<script>

import NewsApiService from './services/NewsApiService'

const API_KEY = '148911f6e11c4568be8c2fb54bc7a938'
const service = new NewsApiService(API_KEY)

const DEFAULT_QUERY = 'javascript'

export default {
  name: 'App',

  data: function() {
    return {
      articles: []
    }
  },

  created: function() {
    service.getNews(DEFAULT_QUERY)
      .then(this.setArticles)
  },

  methods: {
    setArticles: function(articles) {
      this.articles = articles
    }
  }
}
</script>
