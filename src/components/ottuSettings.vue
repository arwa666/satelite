<template>
  <v-card>
    <v-layout>
      <!-- <v-system-bar color="deep-purple darken-3"></v-system-bar> -->

      <v-app-bar

        prominent
      >
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
          <!--
        <v-toolbar-title>My files</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn variant="text" icon="mdi-magnify"></v-btn>

        <v-btn variant="text" icon="mdi-filter"></v-btn>

        <v-btn variant="text" icon="mdi-dots-vertical"></v-btn> -->
        <v-toolbar-title>
        <v-img
          alt="ottu Logo"
          class=""
          cover
          src="../assets/ottu-logo.svg"
          transition="scale-transition"
          width="97px"
      /></v-toolbar-title>
      <v-list>
          <v-list-item>
            <a class="item-list-main" href="/ottu-transactions">
                  <v-list-item-title>
                    <img src="../assets/overview.svg" /><span
                      >overview</span
                    ></v-list-item-title
                  >
              </a>
          </v-list-item>
          <v-list-item>
            <a class="item-list-main" href="/ottu-transactions">
                  <v-list-item-title>
                    <img src="../assets/subscriptions.svg" /><span
                      >Subscriptions</span
                    ></v-list-item-title
                  >
              </a>
          </v-list-item>
          <v-list-item>
            <v-menu>
              <template v-slot:activator="{ props }">
                <v-btn
                  color=""
                  v-bind="props"
                  append-icon="$expand"
                >
                <img src="../assets/reports.svg" />
                Reports
                </v-btn>
              </template>
              <v-list>
                <v-list-item
                  v-for="(item, index) in items2"
                  :key="index"
                  :value="index"
                >
                  <v-list-item-title>{{ item.title }}</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-menu>
          </v-list-item>
          <v-list-item>
            <a class="item-list-main" href="/ottu-transactions">
                  <v-list-item-title>
                    <img src="../assets/settings.svg" /><span
                      >Settings</span
                    ></v-list-item-title
                  >
              </a>
          </v-list-item>
        </v-list>
      </v-app-bar>

      <v-navigation-drawer
        v-model="drawer"
        location="left"
        temporary
      >
      <v-list>
          <v-list-item>
            <a class="item-list-main" href="/ottu-transactions">
                  <v-list-item-title>
                    <img src="../assets/overview.svg" /><span
                      >overview</span
                    ></v-list-item-title
                  >
              </a>
          </v-list-item>
          <v-list-item>
            <a class="item-list-main" href="/ottu-transactions">
                  <v-list-item-title>
                    <img src="../assets/subscriptions.svg" /><span
                      >Subscriptions</span
                    ></v-list-item-title
                  >
              </a>
          </v-list-item>
            <v-list-item class="no-underlay">
               <v-list >
                <v-list-group value="Users">
                  <template v-slot:activator="{ props }">
                    <v-list-item
                      v-bind="props"
                      prepend-icon=""
                      title=""
                    >
                       <img src="../assets/reports.svg" />
                       Reports
                  </v-list-item>
                  </template>


                  <v-list>
                    <v-list-item
                      v-for="([title, icon], i) in admins"
                      :key="i"
                      :title="title"
                      :prepend-icon="icon"
                      :value="title"
                    ></v-list-item>
                  </v-list>
                </v-list-group>
              </v-list>
            </v-list-item>
          <v-list-item>
            <a class="item-list-main" href="/ottu-transactions">
                  <v-list-item-title>
                    <img src="../assets/settings.svg" /><span
                      >Settings</span
                    ></v-list-item-title
                  >
              </a>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-main>
      <v-container>
        <div clas="tran-title">
          <h1>Settings</h1>
          <v-card-text
            style="
            color: #535353
            font-size: 16px !important;
            font-weight: 500;
            padding-left:0
          "
          >
            Modify and configure your Ottu Account Settings
          </v-card-text>
        </div>
        <div class="settings-main">
          <div class="first-set">
            <h2>General</h2>
            <p>Explore your transactions on any of your Ottu installments</p>
          </div>
          <div class="right-set">
          <div class="second-set">
            <v-switch
              :label="`Enable auto-billing for Ottu's services`"
              v-model="switch1"
              inset
              color="primary"
            ></v-switch>
          </div>
          <h2>Allow auto-billing for:</h2>
          <div class="third-set">
            <v-switch
              :label="`Shopify Billing`"
              v-model="switch2"
              inset
              color="primary"
            ></v-switch>
          </div>
          <div class="four-set">
            <v-switch
              :label="`Ottu's Yearly Subscription`"
              v-model="switch3"
              color="primary"
              inset
            ></v-switch>
          </div>
          </div>
        </div>
      </v-container>
    </v-main>
    </v-layout>
  </v-card>
</template>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Public+Sans:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
  body,html,span,p,h1,li, a{
    font-family: 'Public Sans', sans-serif !important;
  }
</style>
<style>

  .v-application__wrap > header{
    display:none!important;
  }
  .v-main{
    padding-top: 0px!important;
  }
  .v-toolbar{
    background-color: #302f37!important;
    z-index:900!important;

  }
  .v-toolbar .v-toolbar__content{
    height: 56px!important;
  }
  .v-toolbar__content > .v-toolbar-title {
    margin-inline-start: 16px;
    width: fit-content;
    flex: unset;
}
.v-main .v-container{
  padding-top:100px!important;
}
.v-main .v-card--variant-elevated{
  box-shadow:none!important;
}
header .v-list{
  display: flex;
  margin-inline:auto;
  background-color: transparent;
}
.v-toolbar__content .v-list-item-title{
  display:flex;
  align-items: center;
  color:#fff;
  gap:10px

}
.v-toolbar__content a,
.v-toolbar__content a:hover{
  text-decoration: none;
}
.v-toolbar__content span:nth-child(3){
  display: flex;
  align-items: center;
  color: #fff;
  gap:10px
}
.v-btn__append{
  color:#78777c;
  width:24px;
  height:24px;
  font-size: 24px;
}
.v-toolbar__content .v-list-item__underlay{
  width:calc(100% - 10px);
  height:50px;
  background: linear-gradient(92.59deg, #fd8862 -43.41%, #f77d1a 99.75%);
    border-radius: 10px;
    z-index: -1;
    transition: all .3s ease-in-out;
  left:50%;
  transform: translateX(-50%) scale(0);

}
.v-list-item:hover .v-list-item__underlay{
  transform: translateX(-50%) scale(1);
}
.v-toolbar__content{
  position: relative;
  z-index: 1;
}
.text-primary .v-switch__track{
  background: #FB923C!important;
    opacity: 1;
}
.text-primary .v-switch__thumb{
  background-color: #fff!important;
}
.v-switch .v-selection-control{
  flex-direction: row-reverse;
}
.second-set .v-label{
  font-weight: 600;
    font-size: 14px;
    line-height: 18px;
    color: #1A1A1A;
    padding-top: 18px;
    opacity:1!important;
    padding-inline-start: 0px!important;
}
.v-input__details{
  display:none!important;
}
.third-set .v-label{
  font-weight: 400;
    font-size: 14px!important;
    color: rgba(26, 26, 26, 1)!important;
    opacity:1!important;
    padding-inline-start: 0px!important;
}
.four-set .v-label{
  font-weight: 400;
    font-size: 14px!important;
    color: rgba(26, 26, 26, 1)!important;
    opacity:1!important;
    padding-inline-start: 0px!important;
}
.v-toolbar .v-btn:hover > .v-btn__overlay{
  display:none!important;
}
.v-toolbar .v-btn:focus > .v-btn__overlay{
  display: none!important;
}
@media(min-width:768px){
  .v-app-bar-nav-icon{
    display: none!important;
  }


}
@media(max-width:768px){

  .v-toolbar__content > .v-btn:first-child{
    width:fit-content!important;
  }
  header .v-list{
    display:none;
  }
  .v-toolbar-title{
    margin-inline:auto;
    display:flex;
    margin-inline-start: auto !important;;
  }
  .v-navigation-drawer{
    top:0px!important;
    height: calc(100% - 0px)!important;
  }
  .v-navigation-drawer__content{
    justify-content: flex-start!important;
  }
}
.v-navigation-drawer__content .v-list-item-title{
  display:flex;
  align-items: center;
  gap:10px;
  color: #fff;
  font-size: 14px;
  font-weight: 500;
}
.v-navigation-drawer__content .v-list{
  width:100%;
}
.v-navigation-drawer__content .v-list-item__underlay{
  width:calc(100% - 10px);
  height:50px;
  background: linear-gradient(92.59deg, #fd8862 -43.41%, #f77d1a 99.75%);
    border-radius: 10px;
    z-index: -1;
    transition: all .3s ease-in-out;
  left:50%;
  transform: translateX(-50%) scale(0);

}
.v-navigation-drawer__content .v-list-item:hover .v-list-item__underlay{
  transform: translateX(-50%) scale(1);
}
.v-navigation-drawer__content .v-list-item{
  position:relative;
  z-index: 1;
}
</style>
<style>
/* .v-main {
  padding: 0 50px 0px 50px !important;
} */
.v-menu__content.theme--light.v-menu__content--fixed.menuable__content__active {
  top: 56px !important;
  background: #f9f9f9;
  border: 1px solid #bcbcbc;
  border-radius: 0px 0px 10px 10px;
  box-shadow: none;
}
.v-list-item__title {
  font-weight: 500;
  font-size: 14px;
  color: #828282;
  transition: all 0.3s ease-in-out;
}
.v-list-item__title:hover {
  font-weight: 600;
  font-size: 14px;
  color: #333333;
}
.settings-main{
  border: 1px solid #E2E8F0;
border-radius: 15px;
display: flex;
padding: 29px 36px;
flex-wrap: wrap;
align-items: baseline;
}
.second-set{
border-bottom: 1px solid #E4E6E8;

}
.second-set .v-label.theme--light{
font-weight: 600;
font-size: 14px!important;
color: #171721!important;

}
.right-set h2{
  font-weight: 600;
font-size: 14px;
line-height: 18px;
color: #1A1A1A;
padding-top: 18px;
}
.settings-main .theme--light.v-messages{
  display: none;
}
.third-set  .v-label.theme--light,
.four-set  .v-label.theme--light{
  font-weight: 400;
font-size: 14px!important;
color: rgba(26, 26, 26, 0.88)!important;

}
/* .settings-main .v-input--switch__track.theme--light.primary--text{
 background: #FB923C!important;opacity: 1;

} */
/* .settings-main .theme--light.v-input--switch .v-input--switch__thumb.theme--light.primary--text{
  color: #fff!important;
} */
.first-set h2{
font-weight: 600;
font-size: 18px;
color: #000000;
mix-blend-mode: normal;
opacity: 0.9;
padding-bottom: 15px;
}
.first-set p{
  font-weight: 500;
font-size: 14px;
letter-spacing: 0.2px;
color: #535353;
opacity: 0.7;
}
.settings-main .theme--light.v-input--switch .v-input--switch__thumb{
color: #8083A3;
}
/* .settings-main .v-input--switch--inset .v-input--switch__track{
  background: #F5F5FA;opacity: 1;
} */
.settings-main .v-input__slot{
  flex-direction: row-reverse;
}
.settings-main .v-input--selection-controls .v-input__slot > .v-label, .v-input--selection-controls .v-radio > .v-label{
  width: 100%;
  justify-content: space-between;
}
.settings-main .right-set{
  width: 70%;
}
.settings-main .first-set{
  width: 25%;
}
.page-foot {
  margin-top: 25px;
  justify-content: space-between;
}
.page-foot span {
  font-weight: 500;
  font-size: 12px;
  color: #302f37;
}
.v-pagination.theme--light li:first-of-type {
  display: none;
}


.main-btns {
  display: flex;
  margin-bottom: 10px;
}
.mdi-menu-down::before {
  background-image: url("../assets/Arrow - Down 2.svg");
  content: "";
  width: 24px;
  height: 24px;
}
.v-slide-group__content {
  background: rgba(217, 217, 217, 0.25);
  border: 1px solid #e2e8f0;
  width: 396px !important;
  flex: initial;
  border-radius: 15px;
  height: 44px;
  /* margin-top: 24px; */
}
.report-btn .mdi-menu-down::before {
  /* background-image: url("../assets/More Icon.svg");
  content: "";
  width: 24px;
  height: 24px; */
  filter: brightness(0) invert(1);
}
.v-application a {
  color: #8083a3 !important;
  text-decoration: none;
}

.main-search {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 16px;
  gap: 12px;
  height: 40px;
  background: rgba(217, 217, 217, 0.15);
  border: 1px solid rgba(226, 232, 240, 0.55);
  border-radius: 10px;
}
.sign-form {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.main-filter {
  height: 40px;
  background: rgba(217, 217, 217, 0.15);
  border: 1px solid rgba(226, 232, 240, 0.55);
  border-radius: 10px;
  font-size: 14px;
  font-weight: 700;
  line-height: 21px;
  text-align: center;
  color: #4f4f4f;
}
.v-text-field.v-text-field--enclosed:not(.v-text-field--rounded)
  > .v-input__control
  > .v-input__slot,
.v-text-field.v-text-field--enclosed .v-text-field__details {
  border: 0 !important;
}

body {
  height: 100vh;
}
.mobile-year {
  display: none;
}
/* .v-application .v-toolbar__content > .v-btn.v-btn--icon:first-child,
.v-application .v-toolbar__extension > .v-btn.v-btn--icon:first-child {
  display: none;
} */
.v-toolbar__content,
.v-toolbar__extension {
  background-color: #302f37;
}
.v-sheet.v-app-bar.v-toolbar:not(.v-sheet--outlined) {
  left: 0 !important;
  height: 56px !important;
}
.v-toolbar__content,
.v-toolbar__extension {
  height: 56px !important;
}
.theme--light.v-navigation-drawer {
  display: none;
}
.search-section,
.selects-lists {
  display: flex;
  margin-bottom: 24px;
  flex-wrap: wrap;
  align-items: center;
}
@media (max-width: 1240px) {
  .main-img {
    height: auto !important;
    width: auto !important;
    display: block;
    margin: auto;
  }
  .settings-main .first-set,
  .settings-main .right-set{
    width: 100%;
  }
  /* .v-application .v-toolbar__content > .v-btn.v-btn--icon:first-child,
  .v-application
    .v-toolbar__extension
    > .v-btn.v-btn--icon:first-child {
    display: block;
  } */
  .theme--light.v-navigation-drawer {
    display: block;
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
  /* .v-main{
    padding: 0 15px !important;
  } */
  .main-img {
    width: 100% !important;
  }
  .settings-main{
    padding: 29px 6px;
  }
  .sign-in-title {
    font-size: 30px !important;
  }
  /* .v-btn {
    width: 100% !important;
  } */
}

@media (max-width: 575px) {
  .sign-in-title {
    font-size: 25px !important;
  }
  .second-set .v-label.theme--light,
  .third-set .v-label.theme--light, .four-set .v-label.theme--light {
    font-size: 12px!important;
  }

}
.v-pagination.v-pagination li:last-of-type button {
  position: relative;
  width: 70px;
  display: flex;
  padding-left: 40px;
}
.v-pagination.v-pagination li:last-of-type button:after {
  position: absolute;
  content: "Next";
  top: 3px;
  left: 9px;
}
.v-tabs {
  border-top-left-radius: 15px !important;
  border-bottom-left-radius: 15px;
}
.main-list {
  display: flex;
  background: transparent !important;
  height: 56px;
  align-items: center;
}
.theme--light.v-card {
  background: transparent !important;
}
.v-overflow-btn .v-input__slot {
  border-width: 0;
}
.v-application .v-overflow-btn .v-label {
  color: #fff !important;
}
.report-btn .v-input__control {
  height: 50px;
}
.v-list-item__icon {
  align-self: center;
  margin: 0;
}
.main-list .v-list-item .v-list-item__title,
.main-list .v-list-item .v-list-item__subtitle {
  color: #fff;
  font-size: 14px;
  font-weight: 500;
}
.v-sheet.v-card:not(.v-sheet--outlined) {
  margin: auto;
}
.v-sheet.v-card:not(.v-sheet--outlined) {
  box-shadow: none;
}
.v-tab--active.first-tab {
  border-top-left-radius: 15px;
  border-bottom-left-radius: 15px;
}
.v-tabs .v-tab:first-of-type {
  border-top-left-radius: 15px;
  border-bottom-left-radius: 15px;
}
.v-tabs .v-tab:last-of-type {
  border-top-right-radius: 15px;
  border-bottom-right-radius: 15px;
}
.v-application .v-list-item__action:first-child,
.v-application .v-list-item__icon:first-child {
  margin-right: 5px;
}
.v-application .v-expansion-panel-header {
  background: #ffffff;
  border: 1px solid #e2e8f0;
  border-radius: 14px;
  margin-bottom: 22px;
}
.theme--light.v-expansion-panels .v-expansion-panel:not(:first-child)::after {
  border-color: transparent;
}
/* .v-list-item__content {
  width: 100%;
  height: 56px;
  margin: 0 12px;
} */
.v-input--dense > .v-input__control > .v-input__slot {
  width: 150px;
  height: 37px;
  background: rgba(217, 217, 217, 0.15);
  border: 1px solid rgba(226, 232, 240, 0.5);
  border-radius: 8px;
  font-weight: 400;
  font-size: 13px;
  display: flex;
  align-items: center;
  color: rgba(26, 26, 26, 0.7);
}
@media (min-width: 1400px) {
  .v-input--dense > .v-input__control > .v-input__slot {
    width: 200px;
    font-size: 14px;
  }
}
.mdi-dots-vertical::before {
  color: #302f37 !important;
}
.v-pagination__item.v-pagination__item--active.primary {
  background: rgba(247, 125, 26, 0.19) !important;
  font-weight: 700;
  font-size: 14px;
  line-height: 18px;
  text-align: center;
  color: #292c43;
  box-shadow: none;
}
.v-pagination__item {
  box-shadow: none;
  font-weight: 600;
  font-size: 13px;
  line-height: 18px;
  text-align: center;
  color: #171721;
}
.report-btn .v-select__selection--comma {
  overflow: unset;
  color: #fff;
}
.main-filter.v-select.v-select--is-menu-active .v-input__icon--append .v-icon {
  transform: rotate(0);
}
.main-filter.theme--light.v-select.v-text-field--solo-inverted.v-input--is-focused
  .v-select__selections {
  font-weight: 700;
  font-size: 14px;
  line-height: 21px;
  text-align: center;
  color: #4f4f4f;
}
.main-filter {
  background: rgba(217, 217, 217, 0.25);
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  width: 100%;
  height: 40px;
}
.main-filter.v-text-field.v-text-field--solo .v-label {
  top: calc(50% - 13px);
}
.v-application .v-expansion-panel-header span:first-of-type {
  font-weight: 700;
  font-size: 18px;
  line-height: 24px;
  display: flex;
  align-items: center;
  color: #302f37;
}
.v-application .v-expansion-panel-header span:nth-of-type(2) {
  font-weight: 600;
  font-size: 15px;
  line-height: 21px;
  color: #302f37;
}
.tran-table tr {
  height: 46px;
}
table tr:nth-child(even) {
  background: rgba(217, 217, 217, 0.12);
}
.v-expansion-panel-content
  .theme--light.v-data-table
  > .v-data-table__wrapper
  > table
  > thead
  > tr:last-child
  > th:not(:first-of-type) {
  /* text-align: end!important; */
}
.v-expansion-panel-content
  .theme--light.v-data-table
  > .v-data-table__wrapper
  > table
  > thead
  > tr:last-child
  > th {
  font-weight: 600;
  font-size: 15px;
  color: #302f37;
}
.v-expansion-panel-content
  .v-data-table--dense
  > .v-data-table__wrapper
  > table
  > tbody
  > tr
  > td,
.v-data-table--dense > .v-data-table__wrapper > table > thead > tr > td,
.v-data-table--dense > .v-data-table__wrapper > table > tfoot > tr > td {
  font-weight: 400;
  font-size: 14px;
  color: #262626;
  /* text-align: end!important; */
}
.v-expansion-panel-content
  .v-data-table--dense
  > .v-data-table__wrapper
  > table
  > tbody
  > tr
  > td.amount,
.v-expansion-panel-content
  .v-data-table--dense
  > .v-data-table__wrapper
  > table
  > thead
  > tr
  > td.amount,
.v-expansion-panel-content
  .v-data-table--dense
  > .v-data-table__wrapper
  > table
  > tfoot
  > tr
  > td.amount {
  font-weight: 700;
}
.v-expansion-panel-content
  .v-data-table--dense
  > .v-data-table__wrapper
  > table
  > tbody
  > tr
  > td.type-name,
.v-expansion-panel-content
  .v-data-table--dense
  > .v-data-table__wrapper
  > table
  > thead
  > tr
  > td.type-name,
.v-expansion-panel-content
  .v-data-table--dense
  > .v-data-table__wrapper
  > table
  > tfoot
  > tr
  > td.type-name {
  font-weight: 500;
  /* text-align: start!important; */
}
.check-select.v-input--selection-controls {
  margin-top: 0;
}
.tran-table td {
  font-weight: 400;
  font-size: 14px;
  color: #262626;
}
.order-element {
  font-weight: 600 !important;
  font-size: 14px;
  color: #f77d1a !important;
}
.total-element {
  font-weight: 700 !important;
  font-size: 14px;
  color: #262626 !important;
}
.state-element span {
  font-weight: 600 !important;
  color: #36d399 !important;
  background: rgb(165, 243, 207, 0.2);
  mix-blend-mode: normal;
  border-radius: 4.5px;
  height: 27px !important;
  width: 58px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.v-select .v-chip,
.theme--light.v-chip:not(.v-chip--active) {
  background: #f89750 !important;
}
.report-btn.v-input__append-inner {
  align-items: baseline;
  align-self: center;
  flex-shrink: 0;
  height: 8px;
  margin-top: 0;
  padding: 0px 4px;
  width: 35px;
}
.report-btn.theme--light.v-select .v-select__selections,
.report-btn.theme--light.v-input input,
.theme--light.v-input textarea {
  color: #fff;
}
/* .v-list-item--link:before {
  background: transparent;
}
.theme--light.v-list-item:not(.v-list-item--active):not(.v-list-item--disabled){
  color: transparent;
} */
.item-list-main .v-list-item__title {
  display: flex;
  align-items: center;
  padding: 5px 8px;
  background: transparent;
  gap: 5px;
  justify-content: center;
}

.item-list-main:focus,
.item-list-main:hover {
  background: linear-gradient(92.59deg, #fd8862 -43.41%, #f77d1a 99.75%);
  border-radius: 8px;
  position: relative;
}
.item-list-main:focus:after,
.item-list-main:hover:after {
  opacity: 1;
  position: absolute;
  bottom: -8px;
  height: 3px;
  content: "";
  background: linear-gradient(92.59deg, #fd8862 -43.41%, #f77d1a 99.75%);
  border-radius: 0px 0px 10px 10px;
  width: 65px;
  left: 50%;
  transform: translate(-50%);
}
.report-main {
  display: flex;
  align-items: center;
  height: 33px;
  width: 100%;
}
.report-main .v-label {
  color: #fff !important;
}
.report-main .theme--light.v-select .v-select__selections {
  color: #fff !important;
}
.report-main
  .v-text-field.v-text-field--enclosed:not(.v-text-field--rounded)
  > .v-input__control
  > .v-input__slot,
.v-text-field.v-text-field--enclosed .v-text-field__details {
  padding-left: 5px !important  ;
}
.report-main .mdi-menu-down::before {
  filter: brightness(0) invert(1);
}
.report-main
  .v-input.v-input--hide-details.v-input--is-label-active.v-input--is-dirty.v-input--is-focused.theme--light.v-text-field.v-text-field--single-line.v-text-field--solo.v-text-field--solo-inverted.v-text-field--solo-flat.v-text-field--is-booted.v-text-field--enclosed.v-select.primary--text {
  background: linear-gradient(92.59deg, #fd8862 -43.41%, #f77d1a 99.75%);
  border-radius: 8px;
  position: relative;
  height: 33px;
  align-items: center;
}
.report-main
  .v-input.v-input--hide-details.v-input--is-label-active.v-input--is-dirty.v-input--is-focused.theme--light.v-text-field.v-text-field--single-line.v-text-field--solo.v-text-field--solo-inverted.v-text-field--solo-flat.v-text-field--is-booted.v-text-field--enclosed.v-select.primary--text:after {
  opacity: 1;
  position: absolute;
  bottom: -8px;
  height: 3px;
  content: "";
  background: linear-gradient(92.59deg, #fd8862 -43.41%, #f77d1a 99.75%);
  border-radius: 0px 0px 10px 10px;
  width: 65px;
  left: 50%;
  transform: translate(-50%);
}
.v-input.v-input--hide-details.v-input--is-label-active.v-input--is-dirty.v-input--is-focused.theme--light.v-text-field.v-text-field--single-line.v-text-field--solo.v-text-field--solo-inverted.v-text-field--solo-flat.v-text-field--is-booted.v-text-field--enclosed.v-select.primary--text
  .v-input__control
  .v-input__slot {
  border: 2px solid #f77d1a;
}
.selects-lists
  .v-text-field.v-text-field--solo:not(.v-text-field--solo-flat)
  > .v-input__control
  > .v-input__slot {
  padding: 10px 16px;
  height: 37px;
  background: rgba(217, 217, 217, 0.15) !important;
  border: 1px solid rgba(226, 232, 240, 0.5) !important;
  border-radius: 8px !important;
  box-shadow: none;
}
/* .v-list-item__content.list-report{
  width: 175px;
} */
.v-text-field.v-text-field--solo .v-input__control {
  min-height: 37px;
}

.main-btns.subscription-tabs .v-slide-group__content {
  background: transparent;
  font-weight: 500;
  font-size: 14px;
  color: #828282;
  border: 0;
  border-radius: 0;
  width: 55% !important;
  height: auto;
}
.main-btns.subscription-tabs .v-tabs .v-tab:last-of-type {
  border-radius: 0;
}
.main-btns.subscription-tabs .v-tab--active {
  background: transparent;
  color: #f77d1a !important;
  font-weight: 700;
  font-size: 20px;
}
.main-btns.subscription-tabs .v-tab {
  justify-content: start;
  text-transform: capitalize;
  min-width: auto;
  height: 32px;
}
.main-btns.subscription-tabs .v-tab::before {
  background: transparent;
  display: none;
}
.main-btns.subscription-tabs .v-tab.first-tab {
  border-right: 1px solid rgba(26, 26, 26, 0.4);
}
.main-btns.subscription-tabs
  .theme--light.v-tabs
  > .v-tabs-bar
  .v-tab:not(.v-tab--active),
.theme--light.v-tabs > .v-tabs-bar .v-tab:not(.v-tab--active) > .v-icon,
.theme--light.v-tabs > .v-tabs-bar .v-tab:not(.v-tab--active) > .v-btn,
.theme--light.v-tabs > .v-tabs-bar .v-tab--disabled {
  width: auto;
}
.theme--light.v-text-field--solo-inverted.v-input--is-focused
  > .v-input__control
  > .v-input__slot
  input {
  color: #171721 !important;
}
.state-element-pend span {
  font-weight: 600 !important;
  background: rgba(26, 26, 26, 0.2);
  mix-blend-mode: normal;
  border-radius: 4.5px;
  height: 27px !important;
  width: 85px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  color: rgba(26, 26, 26, 0.6);
}
.tran-table td.due-date:nth-of-type(2) span {
  font-weight: 500;
  font-size: 14px;
  color: #ff0000;
}
.v-navigation-drawer__content{
  background: #302f37;
    display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
.v-navigation-drawer__content .theme--light.v-list-item:not(.v-list-item--active):not(.v-list-item--disabled){
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

}
.v-navigation-drawer__content  .v-list-item{
  flex-direction: column;
}
.theme--light.v-navigation-drawer {
  display: none;
}
/* .v-application .v-toolbar__content > .v-btn.v-btn--icon:first-child,
.v-application .v-toolbar__extension > .v-btn.v-btn--icon:first-child {
  display: none;
} */
.theme--light.v-list-item:hover::before{
  opacity: 0;
}
@media (max-width:991px) {
    /* .v-application .v-toolbar__content > .v-btn.v-btn--icon:first-child,
  .v-application
    .v-toolbar__extension
    > .v-btn.v-btn--icon:first-child {
    display: block;
  } */
    .item-list-main .v-list-item__title {
    justify-content: start!important;
  }
  .theme--light.v-navigation-drawer {
    display: block;
  }
  .report-main .v-input.v-input--hide-details.v-input--is-label-active.v-input--is-dirty.v-input--is-focused.theme--light.v-text-field.v-text-field--single-line.v-text-field--solo.v-text-field--solo-inverted.v-text-field--solo-flat.v-text-field--is-booted.v-text-field--enclosed.v-select.primary--text:after,
  .item-list-main:focus:after, .item-list-main:hover:after{
    display: none;
  }
  .v-sheet.v-card:not(.v-sheet--outlined){
display: none!important;
  }
  .v-toolbar__content .v-btn.v-size--default{
    color: #fff!important;
  }
  .v-application .v-toolbar__content > .v-btn.v-btn--icon:first-child + .v-toolbar__title, .v-application .v-toolbar__extension > .v-btn.v-btn--icon:first-child + .v-toolbar__title{
    padding-left: 0;
  }
    .v-menu__content.theme--light.v-menu__content--fixed.menuable__content__active {
    top: 275px!important;
  }
  .v-toolbar__content .v-btn__content{
    justify-content: start!important;;
  }
  .theme--light.v-btn:hover::before{
    opacity: 0;
  }
  .v-navigation-drawer__content .v-menu__content.theme--light.v-menu__content--fixed.menuable__content__active{
    top: auto!important;;
  }
  .v-toolbar__title{
    overflow: unset;
  }
  .theme--light.v-app-bar.v-toolbar.v-sheet{
    background: #302f37;
  }

  /* .v-toolbar__content,
.v-toolbar__extension {
  background-color: #302f37;
      width:50%!important

} */
}
.report-main .v-input.v-input--hide-details.theme--light.v-text-field.v-text-field--single-line.v-text-field--solo.v-text-field--solo-inverted.v-text-field--solo-flat.v-text-field--is-booted.v-text-field--enclosed.v-select:before{
  content: '';
  background: url('../assets/reports.svg');
  width: 21px;
  height: 25px;
  position: absolute;
  background-repeat: no-repeat;
  background-size: cover;
  top: 7px;
  left: 5px;
}
.report-main .v-text-field.v-text-field--solo .v-label{
  left: 25px!important;
}
.report-main .v-select__selection--comma{
  margin-left: 25px!important;
}
</style>
<style scoped>
@media (min-width: 1904px) {
  .container {
    max-width: 1490px;
  }
}
#head {
  display: block !important;
}
.theme--light.v-application {
  margin-top: 85px;
}

.v-app-bar {
  display: block !important;
}

</style>
<style>
  .v-navigation-drawer .v-list-item__content{
    height:unset
  }
  .v-list-group .v-list-item__underlay{
    display:none;
  }
  .no-underlay .v-list-item__underlay{
    display:none!important;
  }
  .v-list-group .v-list-item{
    padding-inline-start: 0px!important;
  }
  .no-underlay .v-list-item .v-list-item__content{
      display:flex;
      align-items: center;
      margin-inline-start: 0px;
      gap:10px;
      color: #fff;
      font-size: 14px;
      font-weight: 500;
  }
  .no-underlay  .v-list-item__append{
    color: #fff;
  }
  .no-underlay .v-list-item__prepend{
    color:#fff;
  }
  @media(max-width:992px){

    .v-toolbar .v-list-item{
      width: fit-content;
        padding-inline-start: 10px!important;
    padding-inline-end: 10px!important;
    }
    .v-list-item button{
      padding-inline:0px
    }
  }
</style>

<script>
  export default {
    data: () => ({
      drawer: false,
      group: null,
      items: [
        {
          title: 'Foo',
          value: 'foo',
        },
        {
          title: 'Bar',
          value: 'bar',
        },
        {
          title: 'Fizz',
          value: 'fizz',
        },
        {
          title: 'Buzz',
          value: 'buzz',
        },
      ],
      items2: [
        { title: 'Click Me' },
        { title: 'Click Me' },
        { title: 'Click Me' },
        { title: 'Click Me 2' },
      ],
      e1: {state: 'Reports'},
      report: [ { state: 'Reports'},
        { state: 'Transactions' },
        { state: 'lorem' },
        { state: 'lorem' },],
      admins: [
        ['Management', 'mdi-account-multiple-outline'],
        ['Settings', 'mdi-cog-outline'],
      ],
      cruds: [
        {title:"arwa"},
        {title:"amora"}
      ],
        switch1: true,
    switch2: false,
    switch3: false,
    }),

    watch: {
      group () {
        this.drawer = false
      },
    },
  }
</script>
