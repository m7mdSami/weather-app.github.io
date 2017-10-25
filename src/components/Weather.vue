<template>
  <div id="weather">
    <div class="container">
      <div class="row">
        <div class="col-lg-5">
          <div class="form-group">
            <label for="exampleSelect1">select city</label>
            <select class="form-control" v-model="selected" @change="fetchWeather">
                <option value="Egypt" selected>Egypt</option>
                <option value="russian">russian</option>
                <option value="Germany">Germany</option>
                <option value="canada">canada</option>
                <option value="china">china</option>
                <option value="australia">australia</option>
            </select>
          </div>
        </div>

        <div class="col-lg-5">
          <div class="form-group">
            <label for="exampleSelect1">select country</label>
            <select class="form-control" v-model="selected" @change="fetchWeather">
              <option value="city" selected>city</option>
              <option value="cairo">cairo</option>
              <option value="paris">paris</option>
              <option value="london">london</option>
              <option value="los angeles">los angeles</option>
              <option value="Republic of India">Republic of India</option>
            </select>
          </div>
        </div>

        <div class="col-lg-2 d-flex justify-content-center align-items-center">
          <button type="button" class="btn btn-primary" v-on:click="toggle">{{ txtValue }}</button>
        </div>
      </div>

      <div class="row">
        <div class="list-group-item col-lg-12 text-center d-flex justify-content-center">
            <h3>Weather in {{selected}}</h3>
        </div>
        <div class="list-group-item d-flex justify-content-between" v-bind:class="[booleanValue ? 'col-lg-6' : 'col-lg-12']" v-for="(i, index) in city.list" v-if="index < 4">
          {{i.dt_txt}} <span class="d-flex align-items-center"><h5>{{i.main.humidity}}</h5> <h1>°C</h1></span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: 'Weather',
        data () {
          return {
            city: [],
            booleanValue: false,
            selected: 'egypt',
            txtValue: 'G'
          }
        },
        methods: {
          fetchWeather(){
            this.$http.get('http://api.openweathermap.org/data/2.5/forecast?q='+this.selected+'&mode=json&appid=5121f13fd90c7f33f764109bcfc0c9fd').then(function(res){
              this.city = res.body;
            });
          },
          toggle: function(e){
            this.booleanValue = !this.booleanValue;
            if (this.txtValue == 'G') {
              this.txtValue = 'L';
            }
            else {
              this.txtValue = 'G';
            }
          }
        },
        created: function(){
            this.fetchWeather();
        }
    }
</script>

<style>
  .container{
    width:800px
  }
</style>
