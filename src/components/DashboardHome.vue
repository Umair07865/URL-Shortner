<template>
<div>
 <section class=" black lighten-5 white--text " >
     <h1>Paste the URL to be shortend</h1>
       <div class="d-flex pa-5 pl-5  outerDiv ">
    <v-text-field
      
      :rules="rules"
      hide-details="auto"
      outlined
       pa-4
      placeholder="Input URL "
     class="inputField"
     v-model="userUrl"
    ></v-text-field>
     <v-btn
      depressed
      color="primary"
      height="50"
   
      @click="fetchingapi"
    >
      Shrink
    </v-btn>
  

   
  </div>
    <p class="center">Url Shortener is a free tool to shorten a URL use URL Shortener to create a shortened link and use it anywhere</p>
    
  <v-text-field
     
      :rules="rules"
      hide-details="auto"
      outlined
       placeholder="Short URL "
     class="inputField "
   style="    margin-left: 13rem;
"
     v-model="newUrl"
     
    ></v-text-field>
 </section>
 <!--section 2-->
 <section class="section2 d-flex flex-column content-space-between " >
  
   <div class="secondInnerDiv2 pa-9 mt-5 ml-9">
     <h1>Want More? Try Premium Features!</h1>
     <p>Custom short links, powerful dashboard, detailed analytics, API, UTM builder, QR codes, browser extension, 50+ app integrations and support. Only $14/month.</p>
 <v-btn
      depressed
      color="primary"
      height="4rem"
    >
      Go Premium
    </v-btn>

    <span class="d-flex ">
      <a href="#">
    <p>Sign up free at</p>
    <img src="https://financesonline.com/uploads/2019/09/Rebrandly-logo1.png" alt="" style="height:2rem">
  </a>
    </span>

   </div>

   <!--third div-->
      <div class="secondInnerDiv2  pa-9 mt-5 ml-9 newSecondDivClass">
        <div>
<v-icon class="icons">
  mdi-gavel
</v-icon>
<h2>Easy</h2>
<p>Check the amount of clicks that your shortened url received

</p>
        </div>
        <div>
<v-icon class="icons">
  mdi-key-link
</v-icon>
<h2>Shortened</h2>
<p>Use any link, no matter what size, ShortURL always shortens

</p>
        </div>
        <div>
<v-icon class="icons">
 mdi-coffee-maker-check
</v-icon>
<h2>Secure</h2>
<p>It is fast and secure, our service have HTTPS protocol and data encryption</p>
        </div>
        <div>
<v-icon class="icons">
  mdi-shopping-search
</v-icon>
<h2>Statistics</h2>
<p>Check the amount of clicks that your shortened url received</p>
        </div>
        <div>
<v-icon class="icons">
  mdi-hand-front-right
</v-icon>
<h2>Reliable</h2>
<p>All links that try to disseminate spam, viruses and malware are deleted

</p>
        </div>
        <div>
          <v-icon class="icons">
            mdi-monitor-cellphone-star
          </v-icon>
          <h2>Devices</h2>
          <p>Compatible with smartphones, tablets and desktop

</p>
        </div>
               
       </div>
    

  
 </section>
     <v-footer
    dark
    padless
  >
    <v-card
      flat
      tile
      class="indigo lighten-1 white--text text-center"
    >
      <v-card-text>
        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4 white--text"
          icon
        >
         
        </v-btn>

        <div class="d-flex justify-space-between " style=" justify-content:center;width:20rem;margin-left:40%" >
           <v-icon size="24px">
          mdi-facebook
          </v-icon>
           <v-icon size="24px">
          mdi-twitter
          </v-icon>
           <v-icon size="24px">
          mdi-linkedin
          </v-icon>
           <v-icon size="24px">
          mdi-instagram
          </v-icon>
        </div>


        
      </v-card-text>

      <v-card-text class="white--text pt-0">
        Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet. Mauris cursus commodo interdum. Praesent ut risus eget 
        metus luctus accumsan id ultrices nunc. Sed at orci sed massa consectetur dignissim a sit amet dui. Duis commodo vitae 
        velit et faucibus. Morbi vehicula lacinia malesuada. Nulla placerat augue vel ipsum ultrices, cursus iaculis
         dui sollicitudin. Vestibulum eu ipsum vel diam elementum tempor vel ut orci. Orci varius natoque penatibus et magnis
          dis parturient montes, nascetur ridiculus mus.
      </v-card-text>

      <v-divider></v-divider>

      <v-card-text class="white--text">
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</div>

</template>
<script>
export default {
    name:"DashboardHome",
    data(){
      return{
         userUrl:"",
         newUrl:""
      }
    },
    methods:{

        fetchingapi(){
        
                const url = new URL(
    "https://t.ly/api/v1/link/shorten"
);

const params = {
    "api_token": "ZiWUDRjrLPVkNux2SztwAPlML7hGnnLzII2hWHpcDhjMtF0NIxKUcMWaq8Dd",
};
Object.keys(params)
    .forEach(key => url.searchParams.append(key, params[key]));

const headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

let body = {
    "long_url": this.userUrl,
    "domain": "",
    "include_qr_code": false
};

fetch(url, {
    method: "POST",
    headers,
    body: JSON.stringify(body),
}).then(response => response.json().then((data)=>{
    console.log(data);
  this.newUrl = data.short_url

}));

        }

    }
}
</script>
<style>
.inputField{
    width: 50%;
    margin-left: 2rem;
    background-color: white;
    

}
section{
    padding: 4rem;
   padding-left: 20%;
   /* border: 1px solid black; */
}
.outerDiv{

    width: 90%;
}
.section2{
  height: fit-content;
  border:1px solid black;
 padding-top: 10px;
justify-content: center;

}
.secondInnerDiv2{
  border: 1px solid rgb(197, 197, 197);
  height: fit-content;
  width: 70%;

  text-align: center;
}
.newSecondDivClass{
  display: grid;
  grid-template-columns: repeat(3);
  grid-template-rows: repeat(2,9rem);
}
.newSecondDivClass > div{
  transition:  ease-in 1s;
}
.newSecondDivClass > div:hover{
  background-color: rgb(176, 173, 173);
}
.icons:before{
   font-size: 3rem;
}

</style>