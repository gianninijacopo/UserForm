<script setup>
  import {ref} from 'vue'
  let users = ref([]);
  let searchTerm = ref("greg");
  let isLoading = ref(false);
  async function fettchGitHubUsers(){
    const res = await fetch("https://api.github.com/users/");
  }
  async function onSubmit()
  {
    isLoading.value = true;
    users.value = await fetchGitHubUsers()
  }
</script>
<template>
  <form @submit.prevent="onSubmit">
    <div class="mb-3">
      <input type="text" class="form-control" v-model="searchTerm">
    </div>
    <button type="submit" class="btn btn-primary">Submit</button>
  </form>
  <div v-if="isLoading" class="spinner-border" role="status"></div>
  <table class="table">
    <thead>
      <tr>
        <th scope="col">Id</th>
        <th scope="col">Avatar</th>
        <th scope="col">Login</th>
        <th scope="col">Url</th>
      </tr>
    </thead>
    <tbody>
    <tr v-for="user in users" :key="user.id">
      <th scope="row">{{ user.id }}</th>
      <td><img :src="user.avatar_url" width="75" height="75"></td>
      <td>{{ user.login }}</td>
      <td><a :href="user.html_url"></a></td>
    </tr>
    </tbody>
  </table>
</template>