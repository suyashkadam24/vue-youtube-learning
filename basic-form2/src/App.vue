<script setup>
import { reactive } from 'vue';

const errorList= reactive([])


const formObj = reactive({
   email:"",
   name:"",
   phone:"",
   subscribe:false,
   gender:"male",
   isNameValid:true,
});

function validateName(){
   if(formObj.name.length < 3){
      formObj.isNameValid = false;
   } else {
      formObj.isNameValid = true;
   }
}

function handleSubmit(){
   errorList.length = 0; // clear the error list before validation

   if(formObj.name.length < 3) {
      errorList.push("Name should be at least 3 characters long");
   }
   if(formObj.email.length === 0) {
      errorList.push("Email is required");
   }
   if(!formObj.subscribe) {
      errorList.push("Plz subscribe the newsletter");
   }
   // submit
   console.log(formObj);
   if(!errorList.length) {
      alert("Form submitted successfully!");
   }
}

</script>

<template>
   <div id="app" class="container">
      <form v-on:submit.prevent="handleSubmit"> <!-- if we don't use prevent, the page will be reloaded and we won't see the console log -->
         <div class="bg-info p-5 rounded m-5">
            <div class="h2 text-center">Learn Vue - Form</div>
            <hr>
            <div>
               <ul>
                  <li v-for="error in errorList" :key="error" class="text-danger">{{ error }}</li>
               </ul>
            </div>
            <div class="input-group mt-3">
               <span class="input-group-text">Email</span>
               <input type="text" class="form-control" v-model.trim ="formObj.email">
            </div>

            <div class="input-group mt-3">
               <span class="input-group-text">Name</span>
               <input type="text" class="form-control" v-on:blur="validateName()" v-model.trim ="formObj.name">
            </div>
            <div v-if="!formObj.isNameValid" class="text-danger">Name should be atlest 3 letter long</div>

            <div class="input-group mt-3">
               <span class="input-group-text">Phone</span>
               <input type="text" class="form-control" v-model.number ="formObj.phone">
            </div>

            <div class="border p-1 mt-3">
               <label class="form-label">Gender</label><br>
               <div class="form-check form-check-inline">
                  <input class="form-check-input" type="radio" name="gender" id="male" v-model="formObj.gender" value="male">
                  <label class="form-check-label" for="male">Male</label>
               </div>
               <div class="form-check form-check-inline">
                  <input class="form-check-input" type="radio" name="gender" id="female" v-model="formObj.gender" value="female">
                  <label class="form-check-label" for="female">Female</label>
               </div>
               <hr>
               <br>

               <select name="gender" id="gender" v-model="formObj.gender" class="form-select">
                  <option value="male">Male</option>
                  <option value="female">Female</option>
               </select>
            </div>

            <div class="input-group mt-3">
               <input type="checkbox" class="form-check-input" v-model ="formObj.subscribe">
               <label class="form-check-label">&nbsp; Subscribe to NewsLetter</label>
            </div>
            <div class="text-center pt-3">
               <button class="btn btn-secondary m-2 w-50">Submit</button>
            </div>
         </div>
      </form>
   </div>
</template>

<style scoped>

</style>
