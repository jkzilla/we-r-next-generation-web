<template>
<div class='container-fluid'>
  <div id='hero-image' class='row'>
    <div class="img-container1">
      <img :src="homePageData.heroImage" alt="top-image" class="fit-image1">
    </div>
    <div class="row">
      <h2 id="hero-words-positioning" class="col-xs-12"><span id="hero-words">{{homePageData.heroText}}</span></h2>
    </div>
  </div>
  <div class='row'>
    <h1 class="col-12">Who we are</h1>
    <p id="who-we-are-paragraph">{{homePageData.whoWeAreText}} </p>
  </div>
  <div id="read-button-div" class='row'>
    <router-link to="/campinfo" >
      <button type="button" class="btn btn-primary btn-lg read-button">Read more</button>
    </router-link>
  </div>
  <div class="row">
    <div class="col-sm-6 col-xs-12" id="success-left">
      <h1>Success Stories</h1>
      <p id="SSparagragh">{{homePageData.sStories[0].text}}</p>
      <div id="crayon-button-div">
        <img src="static/assets/crayons-min.jpg" alt="crayon image" id="crayon-image"/>
        <router-link to="/successStories">
          <button id="crayon-button" type="button" class="btn btn-primary btn-lg read-button">Read more</button>
        </router-link>
      </div>
    </div>
    <div id="success-right-outer" class="col-sm-6 col-xs-12">
      <div id="success-right">
          <div class="img-container2">
            <img :src="homePageData.sStories[0].imageUrl" :alt="'success story image'" class="fit-image1"/>
          </div>
      </div>
    </div>
  </div>
  <div id='action-carousel' class='row'>
    <carousel :navigationEnabled="true" :perPage="1">
      <slide v-for="(action, index) in homePageData.actionCarousel" :key="index">
        <div class="pad-slide">
          <div class="img-container3">
          <img :src="action" :alt="'carousel image 1' + index" class="fit-image1"/>
          </div>
        </div>
      </slide>
    </carousel>
  </div>
  <div class='row' id='testimonial-header'>
    <h1>Testimonials</h1>
  </div>
  <div class='row' id='testimonial-carousel'>
    <carousel :navigationEnabled="true" :perPage="$mq | mq({mobile: 2, other: 3})">
      <slide v-for="(testimonial, index) in homePageData.testimonials" :key="index">
        <div class="pad-slide">
          <p class="testimonial-text">{{testimonial.text}}</p>
          <div class="img-container4">
            <img :src="testimonial.imageUrl" :alt="'testimonial image 1' + index" class="fit-image1"/>
          </div>
        </div>
      </slide>
    </carousel>
  </div>
  <div class='row' id='signup'>
    <div id="signup-highlight">
      <div id="signup-border">
        <div class="img-container5">
          <img :src="homePageData.signupPic" alt="sign-up pic" class="fit-image1"/>
        </div>
      </div>
    </div>
    <router-link to="/signup">
          <button id="signup-button" type="button" class="btn btn-primary btn-lg">Sign Up</button>
      </router-link>
  </div>
  <div id='partners'>
    <div class='row' id='partners-header'>
      <h1>Partners</h1>
    </div>
    <div class='row' id='partners-images center-block'>
      <carousel :perPage="3" :loop="true" :speed="5000" :autoplay="true">
        <slide v-for="partner in homePagePartners" :key="partner._id.$oid">
          <img :src="partner.companyLogo" v-bind:style="{width: '50%'}"/>
        </slide>
      </carousel>
    </div>
  </div>
</div>

</template>

<script>
  import { Carousel, Slide } from 'vue-carousel';
  import axios from 'axios';
  export default {
    name: 'homePage',
    components: {
      Carousel,
      Slide
    },
    data () {
      return {
        homePageData: {
          sStories: [{text:''}]
        },
        homePagePartners: {}
      }
    },
    created() {
      axios.get('/api/v1/resources/homepage')
      .then(res => {
        this.homePageData = res.data.dataObj,
        this.homePagePartners = res.data.partners
      })
      .catch(console.log)
    }
  }
</script>

<style scoped>

  .row {
  margin-left: 0;
  margin-right: 0;
  }

  .container-fluid {
    padding: 0;
  }
  #hero-image {
    position: relative;
    width: 100%;
    text-align: center;
    margin: 0;
  }
  h2 {
    position: absolute;
    top: 20%;
    left: 50%;
    transform: translate(-50%, -50%)
  }
  h2 span {
    color: white;
    font-family: 'Nanum Pen Script', cursive;
    font: bold;
    letter-spacing: -1px;
    background: rgb(0, 0, 0); /* fallback color */
    background: rgba(0, 0, 0, 0.7);
    padding: 10px;
    white-space: nowrap;
  }
  @media (max-width: 1000px) {
    h2 span { font-size: 25px }
  }
  @media (max-width: 800px) {
    h2 span { font-size: 20px }
  }
  @media (max-width: 500px) {
    h2 span { font-size: 15px }
  }
  #who-we-are-paragraph {
    margin: auto;
    width: 80%;
    text-align: left;
    white-space: pre-wrap;
  }
  #read-button-div {
    text-align: left;
    width: 80%;
    margin: auto;
    padding-top: 30px;
  }
  .read-button {
    background-color:#7DDBD4;
    border-color: #7DDBD4;
    font-size: 18px;
    font-weight: 700;
  }
  #success-carousel{
    margin: auto;
    width: 90%;
  }
  #success-left {
    padding: 2.5% 5% 5% 10%;
    float: left;
  }
  #SSparagragh {
    text-align: left;
  }
  #crayon-image {
    width: 40%;
  }
  #success-right-outer {
    padding-right: 6%;
    padding-left: 0;
    padding: 0% 4% 0 4%;
  }
  #success-right{
    padding: 4% 6% 8% 6%;
    float: left;
    background-color:#7DDBD4;
    border-radius: 10px;
    width:100%;
  }
  #action-carousel {
    width: 80%;
    margin: auto;
    margin-top: 2.5%;
    text-align: center;
  }
  #testimonial-carousel {
    width:85%;
    margin: auto;
    text-align: center;
  }
  .testimonial-text {
    min-height: 110px;
  }
  @media (max-width:850px) {
    .testimonial-text {
      min-height:140px;
      }
  }
  @media (max-width:550px) {
    .testimonial-text {
      min-height:180px;
      }
  }
  .pad-slide {
    width: 90%;
    text-align: center;
    margin: auto
  }
  .img-container1 {
    position: relative;
    padding-bottom: 35.67%;
    height:0;
    overflow: hidden;
    width: 100%;
  }
  .img-container2 {
    position: relative;
    padding-bottom: 66.12%;
    height:0;
    overflow: hidden;
    width: 100%;
  }
  .img-container3 {
    position: relative;
    padding-bottom: 66.22%;
    height:0;
    overflow: hidden;
    width: 100%;
  }
  .img-container4 {
    position: relative;
    padding-bottom: 66.56%;
    height:0;
    overflow: hidden;
    width: 100%;
  }
  .img-container5 {
    position: relative;
    padding-bottom: 43.34%;
    height:0;
    overflow: hidden;
    width: 100%;
  }
  .fit-image1 {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    /* height: auto; */
  }
  .fit-image {
    width: 100%;
  }
  #partners-images {
    text-align: center;
  }
  .partners {
    display: inline-block;
    margin: auto;
    padding: 15px;
  }
  @media (max-width: 600px) {
    .partners {
      padding: 7px
    }
  }
  #signup {
    position: relative;
    text-align: center;
    margin: auto;
    width: 100%;
    background-color: #7DDBD4;
  }
  #signup-highlight{
    width:82%;
    padding: 2.5%;
    margin: auto;
    margin-top: 5%;
    margin-bottom: 4%;
    background-color: white;
    text-align: center;
  }
  #signup-button {
    background-color:#FF9327;
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 4%;
  }
</style>
