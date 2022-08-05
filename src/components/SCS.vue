<template>
  <div>
    <template v-if="!msclicked">
      <v-container>
        <v-row justify="center">
          <v-img 
            lazy-src="https://picsum.photos/id/11/10/6"
            contain
            max-height="50vh"
            src="http://drive.google.com/uc?export=view&id=1g2ZbuyXjO2dhtuIjFubkHdIxz_O8idCZ"
          ></v-img>
        </v-row>
        <v-row align="center" justify="center">
          <v-btn @click="getData"
            elevation="2"
            large
            class="ma-3 pa-3"
            :disabled="msloading"
            style="background-color: #7e7055;"
          >
            <div v-show="!msloading" style="color: #0e0e0e;font-weight: bold;">
              <v-icon>mdi-bottle-wine</v-icon>
              Moonshine
            </div>
            <div v-show="msloading">
              collecting...
            </div>
          </v-btn>
        </v-row>
      </v-container>
    </template>

    <template v-if="msclicked">
      <v-container>
        <v-row justify="center">
          <!--
          <v-img
            contain
            max-height="60vh"
            v-bind:src="resImg.src"
          ></v-img>
          -->
        </v-row>
        <v-row justify="center">
          <p class="text-h3 mt-4">{{profit}}</p>
        </v-row>
        <v-row justify="center">
          <v-simple-table>
            <template v-slot:default>
              <thead>
                <tr>
                  <th class="text-left">
                    Item
                  </th>
                  <th class="text-left">
                    Price(₽)
                  </th>
                </tr>
              </thead>
              <tbody>
                <tr
                  v-for="item in itemList"
                  :key="item.name"
                >
                  <td>{{ item.name }}</td>
                  <td>{{ item.price }}</td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
        </v-row>
        <div style="height: 56px;"/>
        <v-btn @click="back"
          fab
          fixed
          bottom
          right
          style="background-color: #7e7055;color: #0e0e0e"
        >
          <v-icon>
            mdi-arrow-left
          </v-icon>
        </v-btn>
      </v-container>
    </template>
  </div>
</template>

<script>
import axios from 'axios'
//let resImg = new Image();

export default {
  name: 'SCS',

  data: () => {
    return {
      msclicked: false,
      msloading: false,
      profit: null,
      itemList: null,
    }
  },

  methods: {
    getData: function(){
      this.msloading = true;
      axios
        .get('https://script.google.com/macros/s/AKfycbzIbxYHLeTX1G3AI3Prh876OCE8cM5eha0TNZBYcGPn-fpQctkcXpt4FMIfSjNIsFR-/exec')
        .then(function(res){
          console.log(res);
          //resImg.src = res.data.picURL;
          this.profit = res.data.profit;
          this.itemList = res.data.itemList;
          
          this.msclicked = true;
          /*
          resImg.onload = function(){
            this.msclicked = true;
          }
          */
        }.bind(this))
        .catch(function (e) {
          console.log(e);
        });
    },
    back: function(){
      this.msloading = false;
      this.msclicked = false;
    }
  }
}
</script>
