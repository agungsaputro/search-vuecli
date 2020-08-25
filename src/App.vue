<template>
  <div id="app">
    <Header/>
    <Search v-model="searchTerm"/>
    <div class="container mx-auto">
      <div class="flex flex-wrap">
        <div class="md:w-1/3 p-4" v-for="galery in photoList" :key="galery.id">
          <Photocard v-bind:title="galery.title" v-bind:imageurl="galery.thumbnailUrl"/>
        </div>
      </div>
    </div>
    <ResultGrid/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Search from './components/Search.vue'
import ResultGrid from './components/ResultGrid.vue'
import {photos as photosData} from './data'
import Photocard from './components/Photocard.vue'
import dataPhoto from './dummy/photo.json'

export default {
  name: 'App',
  components: {
    Header,
    Search,
    ResultGrid,
    Photocard
  },
  data:() =>({
    searchTerm: '',
    tech:'',
    photos:[],
    photoList: dataPhoto

  }),
  methods:{
    filterPhoto(){
      const searchTerm = this.searchTerm.toLowerCase()
      const tech = this.tech
      let result = photosData

      if(searchTerm){
        result = result.filter(post =>{
          return(
            post.title.toLowerCase().search(searchTerm) >= 0
          )
        })
      }
      if(tech){
        result = result.filter(post => post.tech.indexOf(0) >= 0)
      }

      this.photos = result
    }
  },
  watch:{
    searchTerm: function(){
      this.filterPhoto()
    },
    tech:function(){
      this.filterPhoto()
    }
  },
  created(){
    this.filterPhoto()
  }
  
}
</script>