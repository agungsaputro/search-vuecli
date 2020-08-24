<template>
  <div id="app">
    <Header/>
    <Search v-model="searchTerm"/>
    <ResultGrid/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Search from './components/Search.vue'
import ResultGrid from './components/ResultGrid.vue'
import {photos as photosData} from './data'

export default {
  name: 'App',
  components: {
    Header,
    Search,
    ResultGrid
  },
  data:() =>({
    searchTerm: '',
    tech:'',
    photos:[],
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