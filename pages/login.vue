<template>
  <div class='body-class'>
    <div id="login-h">
      <p>Dust にログイン</p>
    </div>
    <div class="login-form">
      <auth-component service_name="google" v-bind:icon_link="g_ico" to_link="/google_auth" action="google_auth" />
      <!-- <auth-component service_name="twitter" v-bind:icon_link="t_ico" />
      <auth-component service_name="github" v-bind:icon_link="git_ico" />
      <auth-component service_name="microsoft" v-bind:icon_link="ms_ico" /> -->
      <auth-component service_name="mail" v-bind:icon_link="mail_ico" to_link="/mail_auth" />
    </div>
  </div>
</template>

<style scoped>
  #login-h {
    /* background: red; */
    display: flex;
    justify-content: center;
    text-align: center;
    width: 100%;
    margin: 0 auto;
    /* border-bottom: solid 1px gray; */
        border-bottom: 1px solid;
    border-image: linear-gradient(to right, #0004de 0%, #bd5aac 100%);
    border-image-slice: 1;
  }

  #login-h p {
    font-size: 3vw;
    font-family: cursive;

  }

  .body-class {
    /* background: darkblue; */
    width: 60vw;
    height: 30vw;
    margin: 0 auto;
    position: absolute;
    top: 45%;
    left: 50%;
    transform: translate(-50%, -50%);
    /* position: fixed;
  width: 100%;
  height: 100%;
  text-align: center; */
  }

  .login-form {
    /* background: rgb(197, 188, 108); */
    height: 15vw;
    vertical-align: center;
    margin-top: 2%;
    /* position: absolute;
  display: flex;
  flex-direction: column;
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%); */
  }

  /* @media screen and (min-width: 501px) {
  .body-class {
    background: linear-gradient(to left, #333,#eee);
  }

  .login-form {
    background: #2d3436;
    margin: 0px;
    padding: 20px;
    min-width: 400px;
    width: 50%;
    height: auto;
    border: solid 1px #dfe6e9;
    box-shadow: 5px 5px 4px;
    border-radius: 30px;
  }
}

@media screen and (max-width: 500px) {
  .body-class {
    background: #2d3436;
  }

  .login-form {
    background: #2d3436;
    width: 100%;
  }
} */
</style>



<script>
  import firebase from '~/plugins/firebase_auth.js';

  import AuthComponent from "~/components/AuthComponent.vue";
  import google_icon_img from "~/static/google_icon.png";
  import twitter_icon_img from "~/static/twitter_icon.png";
  import github_icon_img from "~/static/github_icon.png";
  import microsoft_icon_img from "~/static/microsoft_icon.png";
  import mail_icon_img from "~/static/mail_icon.png";
  import google_authVue from './google_auth.vue';

  const axios = require('axios');
  export default {
    head: {
      meta: [{
        name: "viewport",
        content: "width=device-width,initial-scale=1.0"
      }, ]
    },
    data: function () {
      return {
        title: 'Auth',
        message: 'this is message.',
        g_ico: google_icon_img,
        t_ico: twitter_icon_img,
        git_ico: github_icon_img,
        ms_ico: microsoft_icon_img,
        mail_ico: mail_icon_img,
      };
    },
    components: {
      AuthComponent,
      google_icon_img,
      twitter_icon_img,
      github_icon_img,
      microsoft_icon_img,
      mail_icon_img,
    },
    method: {
      google_auth: function (event) {
        firebase.login_g_auth(this.$store);
      }
    }
  };
</script>