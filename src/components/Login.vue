<template>
  <v-container fluid >
    <v-row  class="mobile-row">
      <v-col sm="12" md="12" lg="6" cols="12" style="padding-top: 0px;">
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
      <v-col class="sign-form"  sm="12" md="12" lg="6" cols="12" style="padding-top: 0px;">
        <div
          class="login"
          style="
            box-shadow: 0px 0px 25px rgba(0, 0, 0, 0.04);
            padding: 64px 60px 56px;
            border-radius: 15px;
            margin: auto;
            width: 557px;
          "
        >
          <h1 class="sign-in-title font-weight-bold mb-3">
            Sign In to your account
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
            Enter your details to proceed further
          </p>
          <v-col>
            <v-text-field
              class="input-main"
              label="Email"
              append-icon="mdi-email-outline"
              v-model="email"
              style="color: #8083a3; font-size: 14px; font-weight: 500"

            ></v-text-field>

          </v-col>
          <v-col>
            <v-text-field
              class="input-main"
              label="Passowrd"
              append-icon="mdi-lock-outline"
              filled
            ></v-text-field>
          </v-col>
          <div class="d-flex justify-end">
            <router-link to="/reset">Forget Password?</router-link>
          </div>
          <div class="d-flex justify-center">
            <v-btn
              style="
                background-color: #fb923c;
                width: 420px;
                height: 54px;
                color: #fff;
                margin-top: 52px;
              "
            >
              Sign In
            </v-btn>
          </div>
        </div>

        <v-card-text
          class="main-year"
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
  @import url('https://fonts.googleapis.com/css2?family=Public+Sans:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
  body,html,span,p,h1,li, a{
    font-family: 'Public Sans', sans-serif !important;
  }
</style>
<style>

.v-text-field.v-text-field--enclosed:not(.v-text-field--rounded)
  > .v-input__control
  > .v-input__slot,
.v-text-field.v-text-field--enclosed .v-text-field__details {
  border: 1px solid #e4e6e8 !important;
  background: transparent;
  border-radius: 10px;
}
.v-text-field.v-text-field--enclosed .v-text-field__details {
  border: 0 !important;
}
.v-application a {
  color: #8083a3 !important;
  text-decoration: none;
}
.theme--light.v-input input,
.theme--light.v-input textarea {
  color: #171721;
  font-size: 14px;
  font-weight: bold;
}
.v-text-field:focus {
  border-color: #e4e6e8;
}
.sign-form {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.v-input.v-input--is-focused > .v-input__control > .v-input__slot:after {
  display: none;
}
.v-icon.v-icon.primary--text {
  color: #171721 !important;
}
.theme--light.v-text-field > .v-input__control > .v-input__slot:before {
  border-color: transparent !important;
}
.v-label {
  font-weight: 500;
  font-size: 14px !important;
  color: #8083a3 !important;
}
.v-label.v-label--active.theme--light {
  font-weight: 500;
  font-size: 14px !important;
  color: #8083a3 !important;
  transform: translateY(-10px) scale(1) !important;
}
.input-main.v-input.v-input--is-focused.theme--light
  > .v-input__control
  > .v-input__slot {
  border: 2px solid #fb923c !important;
}
.input-main .v-field--variant-filled .v-field__overlay{
  background-color:transparent;
}
.input-main{
  border: 1px solid #e4e6e8;
  border-radius: 10px;
  padding-inline-end:16px;
}
.input-main:focus{
  border: 2px solid #fb923c !important;
}
.v-text-field .v-input__details {
   display: none!important;
}
.input-main .v-field__outline{
  display:none
}
.v-main{
  padding-top: 0px!important;
}
.main-year{
  flex:unset!important;
}
.v-theme--light.v-icon {
    color: rgba(0, 0, 0, 0.54);
}
body {
  height: 100vh;
}
.col {
  padding: 0 12px;
}
.sign-in-title {
  color: #171721;
  font-size: 36px !important;
  text-align: center;
}
.mobile-year {
  display: none;
}
@media (max-width: 1240px) {
  .main-img {
    height: auto !important;
    width: auto !important;
    display: block;
    margin: auto;
  }
  .bg-main{
    padding: 50px;
    height: auto!important;
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
    width: 100% !important;
  }
  .sign-in-title {
    font-size: 30px !important;
  }
  .v-btn {
    width: 100% !important;
  }
}
@media (max-width: 575px) {
  .sign-in-title {
    font-size: 25px !important;
  }
}
.bg-main {
  background: #2a2a33;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.col-12{
height: 100vh;
padding: 0px 12px 0px;}
@media(max-width:1200px){
  .sign-form{
  margin-bottom:50px;
  margin-top: 50px;
}
}
</style>
<style >
.v-app-bar {
  display: none !important;
}
#head {
  display: none !important;
}
</style>

<script>
import imgUrl from "../assets/bg-main.svg";



 export default{
  name:"log-in",
   data(){
    return{
      img:imgUrl,
      email:"Name@gmail.com"
    }
   }
 }
</script>
