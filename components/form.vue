<template>
    <div>
    <v-card>
        {{ registrations }}
    <v-card-title>Registration Form</v-card-title>
   
    <div id="fields">
    <v-row>
    <v-col cols="12" md="6">
        <v-text-field v-model="name" label="Please enter your name"></v-text-field>
    </v-col>
    <v-col cols="12" md="6">
    <v-text-field v-model="age" type="number" label="Your age"></v-text-field>
    </v-col>
    </v-row>
    </div>
     <div id="fields">
    <v-row>
    <v-col cols="12" md="6">
        <v-select 
        v-model="selectedRegion" 
        :items="regionResponseData" 
        item-text="name"
        item-value="id"
        label="Please select your region"></v-select>
    </v-col>
    <v-col cols="12" md="6">
    <v-select 
    v-model="gender" 
    :items="gender"
    label="Your gender"></v-select>
    </v-col>
    </v-row>
    </div>
     <div id="fields">
    <v-row>
    <v-col cols="12" md="6">
        <v-text-field v-model="email" label="Enter your email address"></v-text-field>
    </v-col>
    <v-col cols="12" md="6">
    <v-text-field v-model="phoneNumber" label="Your phone number"></v-text-field>
    </v-col>
    </v-row>
    </div>
    <div id="submit">
 <!--Upon clicking it adds the user to the data base-->
    <!-- <v-btn color="primary" @click="addUsers()">Submit</v-btn> -->
    <v-dialog
      v-model="dialog"
      persistent
      width="500"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
        >
          Submit
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="text-h5 grey lighten-2">
            Upload File?
        </v-card-title>

        <v-card-text>
        Do you wish to proceed?
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            text
            @click="closeDialog()"
          >
            Cancel
          </v-btn>
          <v-btn
            color="primary"
            text
            @click="addUsers()"
          >
            Proceed
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    </div>
    </v-card>
    </div>
</template>
<script>
import axios from "axios";
export default {
    data(){
        return {
        dialog:false,
        name:[],
        registrations:[],
        age:[],
        selectedRegion:[],
        gender:[],
        email:[],
        phoneNumber:[],
        regionResponseData:[],
        gender:["male","female"]
    }
     },
    // You want to access data
    mounted(){
    this.getRegions();
    },
    methods:{
      getRegions(){
    axios.get("http://localhost:4000/regions")
    .then(
        res =>{
        this.regionResponseData=res.data;
        console.log("region response",res.data);
        })
      },
    //A function addUsers has been created, it has an object user with certain details
    addUsers(){
        debugger;
        axios.post("http://localhost:4000/registrations",{
        headers: {
            "Content-Type":"application/json"
        },
        payload:{
        "name": this.name,
        "age": this.age,
        "region": this.selectedRegion,
        "gender":this.gender,
        "email":this.email,
        "phoneNumber": this.phoneNumber
        }
        });
        this.name=[],
        this.age=[],
        this.selectedRegion=[],
        //We cant empty this one cause we need to select our gender
        this.email=[],
        this.phoneNumber=[]
        this.dialog=false;
        alert("File has been submitted successfully");
    },
    closeDialog() {
    this.dialog=false
    }
}
}
</script>
<style scoped>
#fields{
    padding-left:2em;
    padding-right:2em;
    padding-bottom:1em;
}
#submit{
    padding-left:2em;
     padding-bottom:1em;
}
</style>