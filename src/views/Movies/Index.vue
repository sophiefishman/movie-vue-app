<template>
  <div class="movies-index">
    <nav class="navbar navbar-light bg-light">
      <div class="container-fluid">
        <a class="navbar-brand">Navbar</a>
        <form class="d-flex">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" />
          <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
      </div>
    </nav>
    <h2>Movies</h2>
    <input type="text" v-model="titleFilter" />
    <div class="movie" v-for="movie in filterBy(movies, titleFilter, 'title')" v-bind:key="movie.id">
      <router-link :to="`/movies/${movie.id}`">
        <h4>{{ movie.title }} ({{ movie.year }})</h4>
      </router-link>
    </div>
    <br />
    <div class="row">
      <div class="col-sm-6">
        <div class="card">
          <div class="card-body">
            <img
              src="https://akns-images.eonline.com/eol_images/Entire_Site/2021210/rs_1200x1200-210310060443-1200-Adam-Driver-Lady-Gaga.jpg?fit=around%7C660:372&output-quality=90&crop=660:372;center,top"
              class="card-img-top"
              alt="..."
            />
            <h5 class="card-title">Adam Driver</h5>
            <p class="card-text">pictured with Lady Gaga on set of House of Gucci</p>
          </div>
        </div>
      </div>
      <div class="col-sm-6">
        <div class="card">
          <div class="card-body">
            <img
              src="https://i.guim.co.uk/img/media/b006f516ad7b38953bbb5052f8dfbef6fc12ce54/0_257_3328_1997/master/3328.jpg?width=445&quality=45&auto=format&fit=max&dpr=2&s=60360418892f245ba4d9531632312959"
              class="card-img-top"
              alt="..."
            />
            <h5 class="card-title">Elliot Page</h5>
            <p class="card-text">we love Elliot Page</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Vue2Filters from "vue2-filters";
export default {
  mixins: [Vue2Filters.mixin],
  data: () => ({
    movies: [],
    titleFilter: "",
  }),
  created: function () {
    axios.get("/movies").then((response) => {
      this.movies = response.data;
      console.log(response.data);
    });
  },
  methods: {},
};
</script>
