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
          <h1>Transactions</h1>
          <v-card-text
            style="
            color: #535353
            font-size: 16px !important;
            font-weight: 500;
                        padding-left:0

          "
          >
            Explore your transactions on any of your Ottu installments
          </v-card-text>
        </div>
        <div class="search-section">
          <div  class="search-input">
            <v-text-field
              class="main-search"
              v-model="search1"
              clearable
              flat
              solo-inverted
              hide-details
              prepend-inner-icon="mdi-magnify"
              placeholder="Search by name, email or phone number..."
            ></v-text-field
          ></div>

            <v-select
              class="main-filter"
              v-model="sortBy"
              flat
              solo-inverted
              hide-details
              :items="keys"
              append-icon="mdi-filter"
              label="Filters"
            ></v-select
          >
        </div>
        <div class="selects-lists">
            <v-select :items="items" label="Plugin Type" class="select-style" dense solo></v-select>
            <v-combobox
            v-model="select"
            :items="items"
            placeholder="Installment"
            multiple
            chips
            class="combo-style"

          ></v-combobox>
          <v-checkbox
            class="check-style"

            :label="`select all`"
          ></v-checkbox>
          <v-select :items="items" label="Payment Gateway" class="select-style" dense solo></v-select>
          <v-select :items="items" label="Pending" class="select-style" dense solo></v-select>
          <v-select :items="items" label="Creation Date" class="select-style" dense solo></v-select>
          <v-select :items="items" label="Modify Date" class="select-style" dense solo></v-select>
        </div>
        <v-tabs
      v-model="tab"

    >
    `      <v-tab value="one"> SUMMARY</v-tab>
          <v-tab value="two">DETAILS</v-tab>
          <div class="right">
            <v-btn class="print-btn" small @click="printSection">
            <span> Print</span> <img src="../assets/print.svg" />
          </v-btn>
          <v-btn class="export-btn">
            <span> Export</span><img src="../assets/export.svg"
          /></v-btn>
          </div>
        </v-tabs>


          <v-window v-model="tab">
            <v-window-item value="one">
              <v-expansion-panels variant="accordion">
              <v-expansion-panel
                v-for="i in 5"
                :key="i"
              >
              <v-expansion-panel-title expand-icon="mdi-chevron-down " collapse-icon="mdi-chevron-down ">
                <span> Online.hashi.com</span>
                <span>View More</span>
            </v-expansion-panel-title>
            <v-expansion-panel-text>

                  <v-table density="compact" class="summary-table">
                    <thead>
                      <tr>
                        <th class="text-left">
                          Type
                        </th>
                        <th class="text-left">
                          Count
                        </th>
                        <th class="text-left">
                          Amount
                        </th>
                        <th class="text-left">
                          Currency
                        </th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr
                        v-for="item in items1"
                        :key="item.type"
                      >
                        <td>{{ item.type }}</td>
                        <td>{{ item.count }}</td>
                        <td>{{ item.amount }}</td>
                        <td>{{ item.currency }}</td>
                      </tr>
                    </tbody>
                  </v-table>


            </v-expansion-panel-text>
            </v-expansion-panel>
            </v-expansion-panels>
            </v-window-item>

            <v-window-item value="two">
              <v-table class="details-table">
              <thead>
                <tr>
                    <th class="text-left">Order No.</th>
                    <th class="text-left">Created</th>
                    <th class="text-left">Total</th>
                    <th class="text-left">Currency</th>
                    <th class="text-left">Type</th>

                    <th class="text-left">
                        Gateway
                    </th>

                    <th class="text-left">Status</th>
                    <th class="text-left">Merchant ID</th>

                    <th class="text-left">Operation</th>
                    <th class="text-left">Modified</th>
                    <th class="text-left">Actions</th>
                  </tr>
              </thead>
              <tbody>
                <tr
                  v-for="item in items3"
                  :key="item.order"
                >
                  <td>{{ item.order }}</td>
                  <td>{{ item.created }}</td>
                  <td>{{ item.total }}</td>
                  <td>{{ item.currency }}</td>
                  <td>{{ item.type }}</td>
                  <td><img src="../assets/Union.svg"/></td>
                  <td class="status__td"><span>{{ item.status }}</span></td>
                  <td>{{ item.merchant }}</td>
                  <td>{{ item.operation }}</td>
                  <td>{{ item.modified }}</td>
                  <td class="actions">
                    <v-menu>
                    <template v-slot:activator="{ props }">
                      <v-btn
                        color=""
                        v-bind="props"
                      >
                      <v-icon>mdi-dots-vertical</v-icon>
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
                  </td>
                </tr>
              </tbody>
            </v-table>
            <div class="bottom">
              <div class="text">Showing 8 of 65 elements</div>
              <v-pagination
              v-model="page"
              :length="4"
              rounded="0"
            ></v-pagination>
            </div>
            </v-window-item>

          </v-window>

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
/* .search-section .v-input__control{
  width:100%;
}
.main-search {
  padding:0px!important;
}
.main-search .v-field__field{
  height:40px
}
.main-search .v-field{
  padding-inline:0px;
}
.main-search input{
  padding-top :0px;
  padding-bottom:0px;
  min-height:40px;
} */
.main-search .v-field{

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
.main-filter{
  background: rgba(217, 217, 217, 0.15);
  border: 1px solid rgba(226, 232, 240, 0.55);
  border-radius: 10px;
  height:40px;
  display: flex;
  align-items: center;
  width:200px
}
.v-field__outline{
  display: none!important;;
}
.main-search .v-field__prepend-inner{
  padding-top: 0px;
}
.main-filter .v-field__overlay{
  display:none;
}
.v-field__overlay{
  display:none;
}
.v-toolbar .v-list-item__content{
  display: flex;
  align-items: center;
}
.main-filter .v-label{
  top:50%!important;
  transform: translateY(-50%);
}
.main-filter .v-field__append-inner{
  padding-top:0px;
  display:flex;
  align-items: center;
}
.main-filter .v-input__append{
  padding-top:0px;
  margin-inline-start: 0px;
  margin-inline-end: 15px;
}
.main-filter .v-field__input{
  padding-top:0px;
  padding-bottom: 0px;
  min-height: 40px;
}
.main-filter input{
  top:50%;
  transform: translateY(-50%);
}
 .bottom{
  display:flex;
  align-items: center;
  justify-content: space-between;
  margin-top:25px;
}

.v-pagination__next{
    position: relative;
    width: 70px;
    display: flex;
    padding-left: 40px;
    box-shadow: 0px 3px 1px -2px rgb(0 0 0 / 20%), 0px 2px 2px 0px rgb(0 0 0 / 14%), 0px 1px 5px 0px rgb(0 0 0 / 12%);

}
.v-pagination__next:after {
    position: absolute;
    content: "Next";
    top: 11px;
    left: 9px;
}
.v-pagination{
  min-width:500px
}
.v-pagination__item--is-active{
  background: rgba(247, 125, 26, 0.19) !important;
    font-weight: 700;
    font-size: 14px;
    line-height: 18px;
    text-align: center;
    color: #292c43;
    box-shadow: none;
}
.v-pagination__item{
  border-radius:4px;
}
v-pagination__next  .v-btn__overlay,
v-pagination__next  .v-btn__underlay{
  display: none!important;
}
v-pagination__prev  .v-btn__overlay,
v-pagination__prev  .v-btn__underlay{
  display: none!important;
}
.v-pagination__item  .v-btn__overlay,
.v-pagination__item  .v-btn__overlay{
  display:none!important

}
.text{
  font-weight: 500;
    font-size: 12px;
    color: #302f37;
}
</style>
<style>
.search-input{
  width: calc(100% - 200px)
}





.mdi-menu-down::before {
  background-image: url("../assets/Arrow - Down 2.svg");
  content: "";
  width: 24px;
  height: 24px;
}



.search-section,
.selects-lists {
  display: flex;
  margin-bottom: 24px;
  align-items: center;
  gap: 10px;
}

.selects-lists {
  flex-wrap: wrap;
}

.mdi-dots-vertical::before {
  color: #302f37 !important;
}


.v-navigation-drawer__content {
  background: #302f37;

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
  .select-style{
    max-width:200px;
    background: rgba(217, 217, 217, 0.15);
    border: 1px solid rgba(226, 232, 240, 0.55);
    border-radius: 10px;
    width: 200px;

  }
  .select-style  .v-field__input{
    padding-top: 10px;
    padding-bottom: 10px;
    min-height: 40px;
  }
  .select-style .v-label.v-field-label{
    top:50%!important;
    transform:translateY(-50%)
  }
  .select-style .v-field__append-inner{
    padding-top:0px;
    display:flex;
    align-items: center;
  }
  .combo-style{
    max-width: 411px;
    background: rgba(217, 217, 217, 0.15);
    border: 1px solid rgba(226, 232, 240, 0.55);
    border-radius: 10px;
  }
  .combo-style  .v-field__input{
    padding-top: 0px;
    padding-bottom: 0px;
    min-height: 40px;
  }
  .combo-style  .v-label.v-field-label{
    top:50%!important;
    transform:translateY(-50%)
  }
  .combo-style .v-field__append-inner{
    padding-top:0px;
    display:flex;
    align-items: center;
  }
  .combo-style input{
    position:relative;
    top:10px
  }
  .combo-style .v-chip__underlay{
    background-color:transparent!important
  }
  .combo-style .v-chip{
    background-color:#f89750
  }
  .v-combobox__selection{
    display: flex;
    align-items: center;
  }
  .check-style{
    max-width:150px
  }
  .v-tabs button{
    min-width:197px!important;
    height:42px
  }
  .v-tabs button .v-btn__underlay{
    background-color: rgba(246,246,246);
    z-index:-1
  }
  .v-slide-group-item--active  .v-btn__underlay{
    background-color: rgb(48,47,55)!important;

  }
  .v-slide-group-item--active .v-btn__content{
    color:#fff!important
  }
  .v-slide-group-item--active::after{
    display: none;
  }
  .v-slide-group__content button:first-child{
    border-top-left-radius: 15px!important;
    border-bottom-left-radius: 15px!important;
    overflow: hidden;
  }
  .v-slide-group__content button:nth-child(2){
    border-top-right-radius: 15px!important;
    border-bottom-right-radius: 15px!important;
    overflow: hidden;
  }
  .v-expansion-panel-title{
    background: #ffffff;
    border: 1px solid #e2e8f0;
    border-radius: 14px!important;
    margin-bottom: 22px;
  }
  .v-expansion-panel-title button{

  }
  .v-expansion-panel-title__overlay{
    display:none
  }
  .v-expansion-panel::after{
    display:none
  }
  .v-expansion-panel__shadow{
    display:none
  }
  .v-expansion-panel-title{
    display:flex;
    justify-content: space-between!important;
  }
  .v-expansion-panel-title span:nth-child(2){
    font-weight: 700;
    font-size: 18px;
    line-height: 24px;
    display: flex;
    align-items: center;
    color: #302f37;
  }
  .v-expansion-panel-title span:nth-child(3){
    font-weight: 600;
    font-size: 15px;
    line-height: 21px;
    color: #302f37;
    margin-inline-start:auto;
  }
  .v-expansion-panel-title__icon{
    margin-inline-start: unset!important;
  }
  .v-expansion-panel-text__wrapper{
    padding: 0px 24px 16px;
  }
  .summary-table th{
    font-weight: 600!important;
    font-size: 15px;
    color: #302f37!important;
  }
  .summary-table td{
    font-weight: 400;
    font-size: 14px;
    color: #262626;
    border-bottom:none!important;
  }
.v-slide-group {
  margin-bottom: 1rem;
}
.summary-table tr:nth-child(even) {
    background: rgba(217, 217, 217, 0.12);
}
.v-slide-group__content {
  display:flex;
  width:100%
}
.v-slide-group__content .right{
  margin-inline-start: auto;
  display:flex;
  gap:20px
}
.v-slide-group__content .right button{
  width:90px;
  height:40px;
  background: rgba(217, 217, 217, 0.25);
    border: 1px solid #e2e8f0;
    border-radius: 10px!important;
    font-weight: 700;
    font-size: 14px !important;
    text-align: center;
    color: #4f4f4f !important;
    box-shadow: none;
    text-transform: capitalize;
    display: flex;
    align-items: center;
    justify-content: center;
    min-width:unset!important;

}
.v-slide-group__content .right button .v-btn__content{
  gap:6px;
  display:flex;
}
.details-table th{
  color: rgba(0,0,0.6)!important
}
.details-table tr:nth-child(even) {
    background: rgba(217, 217, 217, 0.12);
}
.details-table td:first-child{
  font-weight: 600 !important;
    font-size: 14px!important;
    color: #f77d1a !important;
}
.details-table td:not(:first-child){
  font-weight: 400!important;
    font-size: 14px!important;
    color: #262626!important;
}
.status__td span{
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
.actions button{
   border: none;
   box-shadow: none;
   background: transparent;
}
.actions button .v-btn__underlay,
.actions button .v-btn__overlay{
  display:none
}
.details-table td{
  border-bottom: none!important;
}
.actions button:hover,
.actions button:focus{
  box-shadow:none
}
.v-tab__slider{
    display:none
  }
.v-pagination__list {
  justify-content: end;
}
.details-table th{
    height:32px!important
  }
  .details-table td{
    height:32px!important
  }
@media(max-width:768px){
  .bottom{
    flex-direction: column;
    gap:20px
  }
  h1{
    font-size:22.4px
  }
  .v-card-text{
    font-size:14px!important;
  }
  .v-tab{
    font-size:14px!important
  }

  .details-table th{
    font-size:14px!important
  }
  .details-table td{
    font-size:12px!important
  }
  .text {
    font-size: 10px;
  }
  .v-pagination {
    min-width: 300px;
}
  .v-pagination__list{
    justify-content:center
  }
.v-pagination .v-btn{
  font-size:10px!important;
}
.v-pagination__item {
  width:33.6px;
  height:33.6px
}
.v-pagination__item button{
  width:33.6px;
  height:33.6px!important;
  display:flex;
  align-items: center;
  justify-content: center;
}
.v-pagination__next{
  height:33.6px;
}
.v-pagination__next button{
  height:33.6px!important;
}
.v-pagination__next:after {
 top:6px
}
.search-section{
  flex-direction: column;
}
.search-input{
  width:100%
}
.main-filter{
  width:100%
}
.select-style{
  max-width:unset;
  width:100%
}
.v-slide-group{
  height:unset!important;
}
.v-slide-group__content{
  flex-direction:column;

}
.v-slide-group__content button:first-child {
    border-top-left-radius: 0px!important;
    border-bottom-left-radius: 0px!important;
}
.v-slide-group__content button:nth-child(2) {
    border-top-right-radius: 0px!important;
    border-bottom-right-radius: 0px!important;
}
.right{
  margin-top:20px;
  width:100%
}
.v-slide-group__content  .right button{
  border-top-left-radius: 10px!important;
  border-bottom-left-radius: 10px!important;
  border-top-right-radius: 10px!important;
  border-bottom-right-radius: 10px!important;
}
.v-slide-group__content .right button{
  width:calc(50% - 10px)
}
.v-expansion-panel-title span:nth-child(2){
  font-size: 14px;
}
.v-expansion-panel-title span:nth-child(3){
  font-size: 12px;
}
.summary-table th{
  font-size:12px
}
.summary-table td{
  font-size:10px
}
.v-expansion-panel-title{
  padding:10px!important;
  margin-bottom:10px!important
}
.v-expansion-panel--active > .v-expansion-panel-title{
  min-height:unset!important
}
}
</style>
<script>
  export default {

    data: () => ({
      drawer: false,
      group: null,
      page: 1,
      items1:[
        {
          type:"Payment Request",
          count:255,
          amount:"40,000.000",
          currency:"KWD"
        },
        {
          type:"Real Estate",
          count:255,
          amount:"40,000.000",
          currency:"KWD"
        },
        {
          type:"Booking",
          count:255,
          amount:"40,000.000",
          currency:"KWD"
        }
      ],
      items2: [
        { title: 'Click Me' },
        { title: 'Click Me' },
        { title: 'Click Me' },
        { title: 'Click Me 2' },
      ],
      items3: [
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo:"../assets/Union.svg",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
      {
        order: "12548452",
        created: "22.03.2022",
        total: "120.000",
        currency: "KWD",
        type: "Payment",
        logo: "../assets/logo.png",
        status: "Paid",
        merchant: "online.hashi.com",
        operation: "Purchase",
        modified: "22.03.2022",
        actions: "",
      },
    ],
      e1: {state: 'Reports'},
      report: [ { state: 'Reports'},
        { state: 'Transactions' },
        { state: 'lorem' },
        { state: 'lorem' },],

      switch1: true,
      switch2: false,
      switch3: false,
      tab: null,
      open: ['Users'],
      admins: [
        ['Management', 'mdi-account-multiple-outline'],
        ['Settings', 'mdi-cog-outline'],
      ],
      model: [
      {
        text: "option2",
        color: "blue",
      },
    ],
       select: ['Vuetify', 'Programming'],
        items: [
          'Programming',
          'Design',
          'Vue',
          'Vuetify',
        ],


    }),

    watch: {
      group () {
        this.drawer = false
      },
    },
  }
</script>
