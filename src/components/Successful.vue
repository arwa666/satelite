<template>
  <v-container fluid>
    <v-row class="mobile-row    ">
      <v-col sm="12" lg="6" style="padding-top:0px">
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
      <v-col class="sign-form" sm="12" cols="12" md="12" lg="6">
        <div
                class="login "

          style="
            box-shadow: 0px 0px 25px rgba(0, 0, 0, 0.04);
            padding: 64px 60px 56px;
            border-radius: 15px;
            margin: auto;
            width: 557px;
          "
        >
              <v-col>

            <img style="width: 100%; height: 125px" :src="lock"/></v-col>
                  <h1 class="sign-in-title font-weight-bold mb-3">
            Successfully Enabled!
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
            Your phone number is set to <span style="font-size:14px;font-weight:600;color:#333"> +965-73655752</span> Authentication codes will
            be texted to this number for logging in
          </p>



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
.v-input input:focus,
.v-input input:active,
.v-input textarea:focus,
.v-input textarea:active {
  caret-color: #fb923c !important;
}
.theme--light.v-text-field--outlined .v-input--is-focused {
  color: #fb923c;
  border-color: #fb923c !important;
}
.v-text-field--outlined.v-input--is-focused fieldset,
.v-text-field--outlined.v-input--has-state fieldset {
  border: 2px solid #fb923c !important;
}
body {
    height: 100vh;
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
.main-year{
  flex:unset!important;
}
</style>

<script>
import imgUrl from "../assets/bg-main.svg";
import imgUrl2 from "../assets/Lock.svg"
export default {
  name: "successful-en",

  data: () => ({
    img:imgUrl,
    lock:imgUrl2
  }),
};
</script>
