<script setup>
import {ref} from 'vue'

const email = ref('');
const password = ref('');
const validEmail = ref(false);
const validPassword = ref(false);
const emailMessage = ref('');
const passwordMessage = ref('');

function onSubmit()
{
  validEmail.value = false;
  if(email.value.length < 6)
  {
    emailMessage.value = "Email should be minimum 6 characters";
  }
  else if(email.value.indexOf(''))
  {
    emailMessage.value = "Email cannot contain spaces";
  }
  else
  {
    emailMessage.Value=''
  }
}
</script>
<template>
  <form @submit.prevent="onSubmit">
    <div class="mb-3">
      <label for="exampleInputEmail" class="form-label">Email address</label>
      <input type="email" id="exampleInputEmail" class="form-control" v-model="email">
    </div>
    <div v-if="emailMessage.length > 0" class="alert alert-danger">{{ emailMessage }}</div>
    <div class="mb-3">
      <label for="exampleInputPwd" class="form-label">Password</label>
      <input type="password" id="exampleInputPwd" class="form-control" v-model="password">
    </div>
    <div v-if="passwordMessage.length > 0" class="alert alert-danger">{{ passwordMessage }}</div>
    <button type="submit" class="btn btn-primary">Submit</button>
  </form>
  <div class="card">
    <div class="card-body">
      Email: {{ email }} <br> Password: {{ password }}
    </div>
  </div>
</template>
