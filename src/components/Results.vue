<template>
  <div>
      <div class=" col-lg-4 col-md-12 col-sm-12 p-2 pr-3 float-left" >
          <div class="filter p-2">
              <h2>Filter Results</h2>
              <div class="form-group m-2">
                <label>Name</label>
                <input v-model="searchName" placeholder="Text string" type="text" class="form-control" title="Game name">
              </div>
              <div class="form-group m-2">
                <label>Minimum score</label>
                <input placeholder="1 - 10" type="number" class="form-control" title="Game minimum score">
              </div>
              <div class="form-group mt-2">
                <label>Order By</label>
                <div class="row">
                    <div class="col-12 ">
                      <select class="form-control ">
                          <option value="date">Release date</option>
                          <option value="score">Score</option>
                          <option value="name">Name</option>
                      </select>
                    </div>
                </div>
              </div>
              <div class="row">
                <div class="col-lg-4 col-md-12 col-sm-12"><input type="button" class="btn btn-lg btn-block" value="Reset"></div>
              </div>
          </div>
      </div>
      <div class="col-lg-8 col-md-8 col-sm-12 float-left pl-4 pt-2" >
        <div
        v-for="result in filteredList"
        :key="result.id"
        class="p-0 mb-2 row result"
        v-bind:class="{ 'loading' : loading }"
        >
          <img src="https://via.placeholder.com/150" class="img-fluid col-2 p-0 float-left" alt="Responsive image">
          <div class="p-3 mb-2 col 10t name ">
              <h4>{{result.name}}</h4>

              {{ timestamp(result.first_release_date) }}
              <p>{{result.summary}}</p>
              <span>{{result.rating}}</span>
          </div>
        </div>
      </div>
</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import axios from 'axios'
import moment from 'moment'

export default defineComponent({
  name: 'results',
  props: {
    msg: String
  },
  data () {
    return {
      results: [{ name: 'Loading' }, { name: 'Loading' }, { name: 'Loading' }],
      searchName: '',
      searchScore: '',
      orderBy: '',
      success: false,
      error: false,
      loading: true
    }
  },
  methods: {
    timestamp: function (date: any) {
      return (date === undefined ? '' : moment(date).format('DD/MM/YYYY'))
    }
  },
  async created () {
    // GET request using axios with async/await
    await axios.get('https://public.connectnow.org.uk/applicant-test/')
      .then((response) => {
        this.results = response.data
        this.success = true
      })
      .catch((error) => {
        this.error = true
        console.log(error)
      }).finally(() => {
        this.loading = false
      })
  },
  computed: {
    filteredList () {
      return this.results.filter(result => {
        return result.name.toLowerCase().includes(this.searchName.toLowerCase())
      })
    }
  }
})
</script>

<style scoped lang="scss">
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  /* Add loading styles */
  .loading.name{
    background-color: coral;
    width: 90%;
  }
</style>
