<template>
  <v-app>
    <v-toolbar app>
    <v-toolbar-side-icon></v-toolbar-side-icon>
      <v-toolbar-title class="headline text-uppercase">
        <span>Escribe</span>
        <span class="font-weight-light"> y Habla</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
     <!-- <v-toolbar-items class="hidden-sm-and-down">
      <v-btn flat>Link One</v-btn>
      <v-btn flat>Link Two</v-btn>
      <v-btn flat>Link Three</v-btn>
    </v-toolbar-items> -->
    </v-toolbar>

    <v-content>


      <v-container grid-list-md text-xs-center>
        <v-flex xs12 sm6 md3 align-center text-xs-center>
          <h2 id="txt-header" class="display-3">{{message}}</h2>
          <v-btn block color="success" dark @click.native="playClick"><i class="fas fa-play fa-2x"></i></v-btn>
        </v-flex>
        <v-layout row wrap>
          <v-flex xs6>
            <v-btn block color="error" @click.native="deleteClick"><i class="fas fa-trash fa-2x"></i></v-btn>
          </v-flex>
        <v-flex xs6>
          <v-btn block color="warning" @click.native="bckspaceClick"><i class="fas fa-backspace fa-2x"></i></v-btn>
        </v-flex>
        </v-layout>
      </v-container>
      

      <v-container grid-list-md text-xs-center>
        <v-layout row wrap>
          <ButtonLetter
            @click.native="btnLtrClick"
            v-for="(l, i) in letras"
            :key="'l'+i"    
            color='purple'                   
            :letra="l"
            xs2/>  

        </v-layout>
      </v-container>

      <v-container grid-list-md text-xs-center>
        <v-layout row wrap>
          <ButtonLetter
                @click.native="btnLtrClick"
                v-for="(l, i) in acentos"
                :key="'a'+i"
                color='green'           
                :letra="l"/>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>  
</template>

<script>
import ButtonLetter from './components/ButtonLetter';

export default {
  name: 'App',
  components: {
    ButtonLetter
  },
 data: () => ({
      letras: ["A","B","C","D","E","F","G","H","I","J","K","L","M","N","Ñ","O","P","Q","R","S","T","U","V","W","X","Y","Z"," "],
      acentos: ["Á","É","Í","Ó","Ú"],
      message: ''
    }),
  methods: {
      btnLtrClick: function(event) {
      this.message += event.currentTarget.id;
    },
    bckspaceClick: function(event) {
      this.message = this.message.slice(0, -1);
    },
    deleteClick: function() {
      this.message = "";
    },
    playClick: function() {
      /*eslint no-console: ["error", { allow: ["warn", "error"] }] */
      console.warn(this.message); // returns 'foo'
      window.responsiveVoice.speak(this.message, 'Spanish Latin American Female');
    },
   }
}
</script>
