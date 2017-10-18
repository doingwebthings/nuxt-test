<template>
  <div class="section">
    <div class="container">
      <h2 class="title is-4">Auswahl</h2>
      <a @click="getList()" class="button is-link">Go get something!</a>
      <hr>
      <!--{{ items.results}}-->
      <hr>
      <div class="columns">
        <div class="column is-three-quraters">
          <nav class="panel">
            <a v-for="item in items.results" :key="item.url" @click="getDetail(item.url)" class="panel-block">
              {{ item.name }}
            </a>
          </nav>
        </div>
        <div class="column is-one-quarter">
          <div class="card">
            <div class="card-image">
              <figure class="image is-4by3">
                <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
              </figure>
            </div>
            <div class="card-content">
              <div class="media">
                <div class="media-left">
                  <figure class="image is-48x48">
                    <img src="https://bulma.io/images/placeholders/96x96.png" alt="Placeholder image">
                  </figure>
                </div>
                <div class="media-content">
                  <p class="title is-4">John Smith</p>
                  <p class="subtitle is-6">@johnsmith</p>
                </div>
              </div>

              <div class="content">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus nec iaculis mauris.
                <a>@bulmaio</a>.
                <a href="#">#css</a>
                <a href="#">#responsive</a>
                <br>
                <time datetime="2016-1-1">11:09 PM - 1 Jan 2016</time>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import axios from 'axios'




export default {
  props: [
    'items',
    'myProp'
  ],
  methods: {
    getList: function() {
      axios.get('https://swapi.co/api/people')
        .then(response => {
          this.items = response.data.results
        })
        .catch(e => { this.errors.push(e) })
    },
    getDetail: function(url) {
      console.log(url)
      axios.get('https://swapi.co/api/people')
        .then(response => {
          // this.items = response.data.results

        })
        .catch(e => { this.errors.push(e) })
    }
  }
}
</script>
