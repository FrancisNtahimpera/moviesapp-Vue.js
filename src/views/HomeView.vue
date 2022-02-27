<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0409591">
          <img  class="featured-img" src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse3.mm.bing.net%2Fth%3Fid%3DOIP.Z5SnN-mNMGPyuC9DjiFoDQHaEK%26pid%3DApi&f=1" alt="image film dune">
          <div class="detail">
             <h3>Dune</h3>
                  <p>
                      Lorem ipsum dolor sit, amet consectetur adipisi
                      cing elit. Perferendis iste repellendus reiciendi
                      s sed, inventore necessitatibus animi iusto expl
                      icabo ad maxime deleniti laboriosam iure praesent
                      ium libero. Illo et soluta aliquid cum.
                </p>
               </div>        
      </router-link>
    </div>
    <form  @submit.prevent="SearchMovies()" class="search-box">
      <input type="text" placeholder=" tu cherches quoi " v-model="search"/>
      <input type="submit" placeholder="Search"/>  
    </form>

    <div class="movies-list">
      <div class="movie" v-for="movie in movies"  v-bind:key="movie.ImdbID" >
      <router-link v-bind:to="'/movie/' + movie.imdbID" class="" />
      <div class="product-image">
        <img :src="movie.Poster" alt="Movie Poster">
        <div class="type"> {{ movie.Type }}  </div>
      </div>
      <div class="detail">
        <p class="y">  {{ movie.Year }}  </p>
        <h3> {{ movie.Title }}   </h3>
      </div>
      </div>

    </div>
     </div>
</template>



<script>

import { ref } from 'vue';
import env  from '@/env.js';


export default {
  setup(){

    const search =ref("");
    const movies =ref([]);

    const SearchMovies = () => {
      if(search.value != ""){
         fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
         .then(response => response.json())
         .then(data => {
           movies.value = data.Search ;
           search.value = "";
          
         });

      }
    }

      return {
        
        search,
        movies,
        SearchMovies
      }
  }
}


</script>

 
<style lang="scss">
.home{
      .feature-card {
        position : relative;
        .feature-img {
        
        display : block;
        width: 100%;
        height: 100%;
        object-fit: cover;
         position : relative;
        z-index: 0 ;
         }
         .detail{
           position: absolute;
           left: 0;
           right: 0;
           bottom: 0;
           background-color: rgb(87, 87, 114,0.6);
           padding: 16px;
           z-index: 1;
            }

         h3{
           color: white;
           margin-top:16px ;
           top:10px;

         }
         p{
           color: white;
           
         }

     }
      
}
.search-box{
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding:16px ;
  input{
    display: block; 
    border-radius: 15px;  
    padding: 10px 16px ;
    
    border:none;
    outline: none;
    
    &[type="text"]{
      width:100%;
      color:white;
      background-color: #496583;
      font-size: 20px;
      padding: 10px 16px ;
      margin: 15px;

      &::placeholder{
        color:aquamarine;

      }
      
      &::focus{
        box-shadow:10px 5px 5px purple ;
      }

      &[type="submit"]{
        width:100%;
        max-width:300px;
        border-color:  #428883;
        padding:10px;
        border-radius: 8px;
        color: white;
        font-size:20px;
        text-transform: uppercase;
        transition:0.4s;
      }

      &:active{
        border-color: #388070;
      }
       
    }
    .movie-list{
      display:flex;
      flex-wrap:wrap;
      margin: 0px 8px;
       .movie{
      max-width: 50%;
      flex: 1 1 50% ;
      padding: 16px 8px  ;
      .movie-link{
      display:flex;
      flex-direction : column;
      padding: 16px 8px  ;
      height: 100%;
       .product-image{

      position:relative;
      display: block;
      img{
        display: block;
        width: 100%;
      }
    }

    }
   
    }
    
    }
    
   

  




  
</style>
