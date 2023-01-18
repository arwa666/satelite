<template>
  <v-container fluid>
      <v-row class="mobile-row">
        <v-col sm="12" md="12" lg="6" cols="12">
          <div class="bg-main" style="width: 100%; height: 100vh">
          <div class="img-container">
          <img style="width:500px;height:452px" class="main-img" :src="img" />
          </div>
        </div>
             <v-card-text
          class="mobile-year"
          style="
            color: rgba(26, 26, 26, 0.7);
            font-size: 14px !important;
            font-weight: 500;
            text-align: center;
          "
        >
          @{{ new Date().getFullYear() }} <span>Ottu All Right Reserved.</span>
        </v-card-text>
        </v-col>
        <v-col class="sign-form" sm="12" md="12" lg="6" cols="12">
          <div class="login" style="
                              box-shadow: 0px 0px 25px rgba(0, 0, 0, 0.04);
                              padding: 64px 60px 56px;
                              border-radius: 15px;
                              margin: auto;
                              width: 557px;
                            " >
          <h1 class="sign-in-title font-weight-bold mb-3">
            Two Factor authentication
          </h1>
          <p
            style="
              text-align: center;
              color: #8083a3;
              font-size: 14px;
              font-weight: 400;
            "
            class="subheading font-weight-regular"
          >
            Enter the authorization code we sent to <span style="font-size:14px;font-weight:600;color:#333"> +9954554847968</span>
          </p>
          <div class="two-authentication-factor">
            <v-text-field label="" variant="outlined"></v-text-field>
            <v-text-field label="" variant="outlined"></v-text-field>
            <v-text-field label="" variant="outlined"></v-text-field>
            <v-text-field label="" variant="outlined"></v-text-field>
            <v-text-field label="" variant="outlined"></v-text-field>
            <v-text-field label="" variant="outlined"></v-text-field>
          </div>
          <div><p style="color:#333333;text-align:center;font-size:14px;font-weight:bold;padding-top:12px">Resend Code</p></div>
          <div class="d-flex justify-center">
            <v-btn
              style="
                background-color: #fb923c;
                width: 420px;
                height: 54px;
                color: #fff!important;
                margin-top: 30px;
              "
                            to="/successful"

            >
              Verify
            </v-btn>
          </div>
          </div>
          <v-card-text class="main-year"
          style="
            color: rgba(26, 26, 26, 0.7);
            font-size: 14px !important;
            font-weight: 500;
            text-align: center;
          "
        >
          @{{ new Date().getFullYear() }} <span>Ottu All Right Reserved.</span>
        </v-card-text>
         </v-col>
      </v-row>
  </v-container>
</template>
<style>
.main-year{
  flex:unset!important;
}
  .bg-main {
  background: #2a2a33;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.v-toolbar{
  display: none!important;
}
.v-main{
  padding-top:0px;
}
</style>
<style>
body {
    height: 100vh;
}
.position-relative {
 position: relative;
 }
.v-text-field.v-text-field--enclosed:not(.v-text-field--rounded)
  > .v-input__control
  > .v-input__slot,
.v-text-field.v-text-field--enclosed .v-text-field__details {
  border: 1px solid #e4e6e8 !important;
  background: transparent;
}
.v-text-field.v-text-field--enclosed .v-text-field__details {
  border: 0 !important;
}
.v-application a {
  color: #8083a3 !important;
  text-decoration: none;
}

.v-text-field:focus {
  border-color: #e4e6e8;
}
.sign-form {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.v-input input:focus, .v-input input:active, .v-input textarea:focus, .v-input textarea:active{
  caret-color:#FB923C!important;

}
.theme--light.v-text-field--outlined .v-input--is-focused{
  color: #FB923C;
    border-color:#FB923C!important;

}

.v-text-field--outlined.v-input--is-focused fieldset,.v-text-field--outlined.v-input--has-state fieldset{
  border: 2px solid #FB923C!important;
}
.v-application .warning .v-text-field--outlined.v-input--is-focused fieldset,.v-text-field--outlined.v-input--has-state fieldset{
    border: 2px solid #FF0000!important;

}
.v-application .warning {
  background: transparent!important;
  color: #FF0000;
  border-color: transparent!important;
}
.v-application .success{
  background: transparent!important;
  color: #4caf50 !important;
  border-color: transparent!important;
}
.v-sheet.v-snack__wrapper:not(.v-sheet--outlined){
  box-shadow: none;
}

.v-snack:not(.v-snack--absolute){
  position: absolute;
  height: 50px;
}
.v-snack{
  bottom: -39px;
  position: absolute;
  left: 0;
  /* transform: translate(-40%,0); */
  justify-content: center!important;
}
.v-snack__content{
  text-align: center;
}
.v-application--wrap{
  min-height: auto;
}
.otp-main .v-input.v-input--is-focused.theme--light >.v-input__control > .v-input__slot{
border: 0px solid #FB923C!important;
}
.mobile-year {
  display: none;
}
@media (max-width: 1240px) {
  .main-img {
    height: auto !important;
    width: auto!important;
    display: block;
    margin: auto;
  }
  .mobile-row {
    flex-direction: column-reverse;
  }
  .main-year {
    display: none;
  }
  .mobile-year {
    display: block;
  }
}
@media (max-width: 768px) {
  .login {
    width: 100% !important;
    padding: 25px 15px 15px !important;
  }
    .main-img {
    width: 100%!important;
  }
  .sign-in-title {
    font-size: 30px !important;
  }
.v-btn{
width: 100%!important;
}
}
@media (max-width:575px) {
   .sign-in-title {
    font-size: 25px !important;
  }

}
.v-toolbar{
  display:none
}
.two-authentication-factor{
  display:flex;
  align-items: center;
  gap:8px;
  justify-content: center;
  margin-top: 16px;
}
.two-authentication-factor .v-input{
  max-width: 43px;
  height:56px;
}
</style>
<script>

import imgUrl from "../assets/bg-main.svg";

 export default{
  name: "two-factor-authentication",
   data(){
    return{
      img:imgUrl,
    }
   }
 }
</script>
