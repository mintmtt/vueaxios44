<template>
  <div>
    <h1>User page</h1>
    <input type="button" value="Load Data" @click="loadUser" />
    <!--     
    {{userList}}  -->
    <ul v-for="user in userList" :key="user.id">
      <li>
        <router-link :to="`/userdetail/${user.id}`">
          id:{{ user.id }}, {{ user.username }}
        </router-link>
        ,email:{{ user.email }}
        <!-- ,lat:{{ user.address.geo.lat }},lng:{{
          user.address.geo.lng
        }} -->
      </li>
      <a
        :href="
          'https://www.google.com/maps?q=' +
            user.address.geo.lat +
            ',' +
            user.address.geo.lng
        "
        target="_blank"
      >
        ที่อยู่
      </a>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      userList: null,
    };
  },

  methods: {
    loadUser() {
      let url = "http://jsonplaceholder.typicode.com/users";
      axios
        .get(url)
        .then((response) => {
          this.userList = response.data;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

