<template>
  <div class="footer container-fluid">
    <div id="footer" class="row">
      <div id="footer_top" class="col-lg-12">
        <div class="row">
          <div id="footer_left" class="col-sm-12 col-lg-4">
            <h4>The Company</h4>
            <ul>
              <li><router-link to="/home">Home</router-link></li>
              <li><router-link to="/applications">Applications</router-link></li>
              <li><router-link to="/signup">Sign Up</router-link></li>
              <li><router-link to="/login">Login</router-link></li>
              <li><a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=Y2Q2Y3R7WK46C">Donate</a></li>
              <li><router-link to="/faq">FAQ</router-link></li>
              <li><router-link to="/friends">Friends of WRNG</router-link></li>
            </ul>
          </div>
          <div id="footer_center" class="col-sm-12 col-lg-4">
            <h5>Thank you for your interest in We R NextGeneration, the Charity that Inspires.</h5>
            <h4>Contact Us:</h4>
            <p>16501 Shady Grove Road, #8656, Gaithersburg, MD 20898</p>
            <p>Tel. 1-240-224-3430</p>
            <a href="mailto:info@wearenextgeneration.org?Subject=Contact%20from%20website">info@wearenextgeneration.org</a>
          </div>

          <div id="footer_right" class="col-sm-12 col-lg-4">
            <h4>Connect</h4>
            <div class="row">
              <p>
                <a href="https://www.facebook.com/weRnextgeneration" target="_blank" class="fa fa-facebook" style="font-size: 36px;color:white"></a>&nbsp&nbsp
                <a href="https://twitter.com/WeRNxGen" target="_blank" class="fa fa-twitter" style="font-size: 36px;color:white"></a>&nbsp&nbsp
                <a href="https://www.youtube.com/channel/UC3blpMpnnLT70oTJ7HzYx9w" target="_blank" class="fa fa-youtube" style="font-size: 36px;color:white"></a>&nbsp&nbsp
              </p>
            </div>

          </div>
        </div>
      </div>
      <div id="footer_bottom">
        <p><img src="static/assets/WeRNextGeneration_white.png" alt="WeRNextGeneration Logo" width="100px">&nbsp&nbsp&nbsp&copy&nbspCopyright 2017</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'wernxgFooter',
  data() {
    return {};
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  color: black;
}

/*Footer Styling*/
.footer {
  background-color: #cac8c8;
  color: white;
  height: auto;
  width: 100%;
}

#footer_center > a,
#footer_left > ul > li > a {
  color: white;
}

#footer_left > ul {
  columns: 2;
  -webkit-columns: 2;
  -moz-columns: 2;
  list-style: none;
  margin-left: -40px;
}

#footer_right {
  vertical-align: bottom;
  text-align: center;
}

#footer_bottom {
  text-align: center;
}
</style>
