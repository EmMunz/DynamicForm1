<template>
    <div>
    <v-card>
    <v-card-title>Registration Form</v-card-title>
    <div id="fields">
    <v-row>
    <v-col cols="12" md="6">
        <v-text-field label="Please enter your name"></v-text-field>
    </v-col>
    <v-col cols="12" md="6">
    <v-text-field type="number" label="Your age"></v-text-field>
    </v-col>
    </v-row>
    </div>
     <div id="fields">
    <v-row>
    <v-col cols="12" md="6">
        <v-select label="Please select your region"></v-select>
    </v-col>
    <v-col cols="12" md="6">
    <v-select label="Your gender"></v-select>
    </v-col>
    </v-row>
    </div>
     <div id="fields">
    <v-row>
    <v-col cols="12" md="6">
        <v-text-field label="Enter your email address"></v-text-field>
    </v-col>
    <v-col cols="12" md="6">
    <v-text-field label="Your phone number"></v-text-field>
    </v-col>
    </v-row>
    </div>
    <div id="submit">
    <v-btn color="primary">Submit</v-btn>
    </div>
    </v-card>
    </div>
</template>
<script>
export default {
    
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