<template>
    <div class="container contact-form">
    <h3 class="homeTitle">Data Collection Platform</h3>
    <div class="row">
      <div class="col-md-12">
    <ul class="nav nav-tabs homeNav" id="myTab" role="tablist">
  <li class="nav-item">
    <a class="nav-link active" id="home-tab" data-toggle="tab" href="#home" role="tab" aria-controls="home" aria-selected="true">Twitter Keyword Based</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" id="profile-tab" data-toggle="tab" href="#profile" role="tab" aria-controls="profile" aria-selected="false">Twitter Location Based</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" id="contact-tab" data-toggle="tab" href="#contact" role="tab" aria-controls="contact" aria-selected="false">Twitter Users Based</a>
  </li>
   <li class="nav-item">
    <a class="nav-link" id="rss-tab" data-toggle="tab" href="#rssfeed" role="tab" aria-controls="contact" aria-selected="false">RSS Feeds</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" id="stock-tab" data-toggle="tab" href="#stock" role="tab" aria-controls="stock" aria-selected="false">Search Stocks</a>
  </li>
</ul>
<div class="tab-content" id="myTabContent">
  <div class="tab-pane fade show active" id="home" role="tabpanel" aria-labelledby="home-tab">
    <input type="text" id= "keywords" name="keywords" class="form-control" placeholder="Twitter Keywords seperated by commas" />
  </div>
  <div class="tab-pane fade" id="profile" role="tabpanel" aria-labelledby="profile-tab">
    <input type="text" id = "location" name="location" class="form-control" placeholder="Twitter Location seperated by commas" value="" />
  </div>
  <div class="tab-pane fade" id="contact" role="tabpanel" aria-labelledby="contact-tab">
    <input type="text" id = "users" name="users" class="form-control" placeholder="Twitter Users" value="" />
 </div>
 <div class="tab-pane fade" id="stock" role="tabpanel" aria-labelledby="contact-tab">
    <input type="text" id = "stocks" name="stocks" class="form-control" placeholder="Twitter Stocks" value="" />
 </div>
 <div class="tab-pane fade" id="rssfeed" role="tabpanel" aria-labelledby="rss-tab">
   <input type="text" id="rss_url" name="rss_url" class="form-control" placeholder="RSS Feeds URL" value="" />
 </div>
</div>
<input type="button" class="btn btn-primary homeBtn" name="btnSubmit" @click="postCollection" value="Start Collection"/>
</div>
</div>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  data: () => ({}),
  methods: {
    postCollection () {
      const URL = 'http://localhost:8099/consumer/initiate'
      const DATA = JSON.stringify({'consumer_key': 'Y87MWneNyN18ny32UZQQIg',
        'consumer_secret': '03v1r5GNA5gyfxJMeJIcoJn7PGgCIuXMImP2mMZN5g',
        'token': '326146455-5p0UCnpy7yKSVpp6ibBlVtb3UnjIUBSdRxUgHOkX',
        'token_secret': 'aVJ4xKpWycEk3acf1bGDuygPEzFPh8RPXmsd6fMSU',
        'twitter_keywords': [{'keywords_list': ['Trump']}]})
      axios.post(URL, DATA)
    }
  }

}
</script>
<style scoped>
.homeTitle{
   margin-top: 25px;
  margin-bottom: 25px;
}
.homeNav {
margin-bottom: 15px;
}
.homeBtn{
  margin-top: 15px;
}
</style>
