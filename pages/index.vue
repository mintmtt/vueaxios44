<!-- <template>
  <div class="card">
    <v-card>
      <v-toolbar dark color="#abb0fc">
       <div class="v-application">
      <v-text-field v-model="select" label="Search to Manga "></v-text-field>
      <v-btn class="ma-2" outlined color="black" @click="mg">
        Search
         <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn> 
      </v-btn>
    </div> -->

<!-- <v-btn class="ma-2" rounded color="primary" dark @click="SearchAnime">
          SEARCH
          <v-icon right dark> mdi-cloud-upload </v-icon>
        </v-btn> -->
<!-- <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn> -->
<!-- </v-toolbar>
    </v-card>
    <div>
      <v-carousel>
        <v-carousel-item
          v-for="(item, i) in items"
          :key="i"
          :src="item.src"
          reverse-transition="fade-transition"
          transition="fade-transition"
        ></v-carousel-item>
      </v-carousel>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      items: [
        {
          src:
            'https://64.media.tumblr.com/8afc260a67675b4ec6c3e0328e13cec3/tumblr_phwpnhdwEl1tt6f8lo1_1280.jpg',
        },

        {
          src:
            'https://pbs.twimg.com/media/ELS1UAkUUAIoKQ2?format=jpg&name=large',
        },
        {
          src:
            'https://pbs.twimg.com/media/ELS1UAmUcAIECI6?format=jpg&name=large',
        },
      ],
    }
  },
  watch: {
    search(val) {
      val && val !== this.select && this.selectSelections(val)
    },
  },
  methods: {
    },
    selectSelections(v) {
      this.loading = true
      // Simulated ajax select
      setTimeout(() => {
        this.items = this.states.filter((e) => {
          return (e || '').toLowerCase().indexOf((v || '').toLowerCase()) > -1
        })
        this.loading = false
      }, 500)
      // tabs: null,
    },
  },
}
</script> -->

<template>
  <div>
    <div>
      <v-carousel>
        <v-carousel-item
          v-for="(item, i) in items"
          :key="i"
          :src="item.src"
          reverse-transition="fade-transition"
          transition="fade-transition"
        ></v-carousel-item>
      </v-carousel>
    </div>

    <div class="v-application" style="padding-top: 2rem">
      <v-toolbar dark color="#abb0fc">
        <v-toolbar-title>Manga</v-toolbar-title>
        <v-text-field
          v-model="select"
          color="#abb0fc"
          class="mx-4"
          flat
          hide-no-data
          hide-details
          label="search"
          solo-inverted
        ></v-text-field>
        <v-btn class="ma-2" rounded color="purple" @click="mg">
          SEARCH
          <v-icon right dark> mdi-magnify </v-icon>
        </v-btn>
      </v-toolbar>
    </div>
    <v-divider class="mt-4 mb-4"></v-divider>
    <div max-width="250px" class="d-flex flex-wrap" style="margin-left: 2rem;">
      <v-card
        v-for="manga in results"
        :key="manga.id"
        class="ma-4"
        max-width="250px"
        @click="icuClick(manga)"
      >
        <v-img :src="manga.image_url" class="ma-3"
        max-width="250px" @click="icuClick(manga)"></v-img>
        <v-card-text
          ><h5>ID : {{ manga.mal_id }}</h5></v-card-text
        >
        <v-card-title>
          <h4>{{ manga.title }}</h4></v-card-title
        >

        <!-- <v-card-text v-text="article">
          {{ manga.synopsis }}
        </v-card-text>   -->
      </v-card>
    </div>
        
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      titleList: null,
      url: "https://api.jikan.moe/v3/search/manga?q=${this.select}&page=1",
      items: [
        {
          src:
            'https://64.media.tumblr.com/8afc260a67675b4ec6c3e0328e13cec3/tumblr_phwpnhdwEl1tt6f8lo1_1280.jpg',
        },

        {
          src:
            'https://pbs.twimg.com/media/ELS1UAkUUAIoKQ2?format=jpg&name=large',
        },
        {
          src:
            'https://pbs.twimg.com/media/ELS1UAmUcAIECI6?format=jpg&name=large',
        },
      ],

      select: '',
      results: [],
      ikme: [],
      show: false,
    }
  },
  methods: {
    loadTitle() {
      axios
        .get(this.url)
        .then((response) => {
          this.titleList = response.data
        })
        .catch((err) => {
          console.log(err)
        })
        
    },
    mg() {
      const url = `https://api.jikan.moe/v3/search/manga?q=${this.select}&page=1/`
      axios.get(url).then((res) => {
        console.log(res.data)
        this.results = res.data.results
      })
    },
    icuClick(manga) {
      console.log('MANGA', manga)
      window.location = manga.url
    },
  },
}
</script>




