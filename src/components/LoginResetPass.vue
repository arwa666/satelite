<template>
  <v-container fluid>
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
        class="login "
          style="
            box-shadow: 0px 0px 25px rgba(0, 0, 0, 0.04);
            padding: 64px 60px 56px;
            border-radius: 15px;
            margin: auto;
            width: 557px;
          "
        >
                   <h1 class="sign-in-title font-weight-bold mb-3">
            Two Factor authentication
          </h1>

          <p
            style="
              text-align: center;
              color: #8083a3;
              font-size: 14px;
              font-weight: 400;
              margin-bottom: 50px;
            "
            class="subheading font-weight-regular"
          >
            You must set up two factor authentication to go inline with our
            security guidlines
          </p>
          <label class="phone__label">Phone Number</label>
          <v-col id="phone_number" style="position: relative">
            <v-select
              v-model="select"
              :hint="`${select.state}, ${select.abbr}`"
              :items="items"
              item-title="state"
              item-value="abbr"
              label="Select"
              persistent-hint
              return-object
              single-line
            ></v-select>
            <v-text-field class="phone_num"
              style="font-weight: 700;
               font-size: 14px!important;color:#171721"
              label=""
              append-icon="mdi-phone-outline"
            ></v-text-field>

          </v-col>

          <div class="d-flex justify-center">
            <v-btn
              style="
                background-color: #fb923c;
                width: 420px;
                height: 54px;
                color: #fff !important;
                margin-top: 52px;
              "
              to="/twofa"
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
<style >
.bg-main {
  background: #2a2a33;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.v-main{
  padding-top:0px!important
}
#phone_number {
  border: 1px solid #8083a3;
  width: 420px;
  height: 55px;
  border-radius: 5px;
}
.theme--light.v-select .v-select__selections{
font-weight: 700;
font-size: 14px;
color: #8083A3!important;
}
#phone_number input{
font-size:14px;
font-weight:700

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
body {
  height: 100vh;
}
#phone_number .v-select {
  /* position: absolute;
  top: -5px; */
  width: 100px;
}
.theme--light.v-text-field > .v-input__control > .v-input__slot:before {
  display: none;
}
.v-messages__message {
  display: none;
}
#phone_number .v-label.theme--light {
  top: -40px !important;
  left: -120px !important;
}
#phone_number .v-text-field .v-label--active {
  transform: none!important;
}

.v-text-field > .v-input__control > .v-input__slot:after{
  display: none;
}
#phone_number .v-input.v-input--is-focused.theme--light >.v-input__control > .v-input__slot {
border: 0!important;
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
#phone_number{
  width: 100%;
}
}
@media (max-width:575px) {
   .sign-in-title {
    font-size: 25px !important;
  }

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
</style>
<style >
.v-app-bar {
  display: none !important;
}
#head {
  display: none !important;
}
.phone_num{
  width: calc(100% - 100px);
}
#phone_number{
  display: flex;
  align-items: center;
  padding-inline-start: 0px;
  padding-inline-end:16px;
}
.phone__label{
    font-weight: 500;
    font-size: 14px !important;
    color: #8083a3 !important;
    margin-bottom:15px;
    display: block;
}
#phone_number .v-field--variant-filled .v-field__overlay{
  display:none;
}
</style>


<script>
import imgUrl from "../assets/bg-main.svg";
export default {
  name: "login-reset-passord",


  data() {
    return {
      select: { state: '+965', abbr: 'kw' },
        items: [
        { state: "+965", abbr: "kw" },
        { state: "+963", abbr: "sy" },
        { state: "+961", abbr: "lb" },
        ],
      img:imgUrl

    };

  },
};
</script>
