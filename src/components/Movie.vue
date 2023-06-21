<template>

  <div>

    <h1 id="movie-title">{{ movie.movie_title }}</h1>
    <div class="img-box">
      <img class="movie-poster" :src="movie.img_url" />
    </div>

  </div>

</template>

<script>

export default {
    props: {
        movie: Object
    }
}

</script>

<style scoped>

.img-box{
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

#movie-title{
  color: white;
  font-family: 'Kodchasan', sans-serif;
  font-weight: normal;
  display: flex;
  justify-content: center; 
  align-items: center; 
  font-size: 2.4rem;
  margin: 2% auto;
}

.movie-poster {
  max-height: 800px;
  max-width: 300px;
  display: block;
  box-shadow: 0px 0px 20px 2px #F84AA7;
  margin: 10px;
  border-radius: 10px;
}

</style>