<template>
  <div class="show-content">
    <h2>
      in this tutorial i wanna try to teach you how fetch api with vue 3 script
      setup
    </h2>
    <p>
      <a href="https:github.com/shomalikhashayar"
        >check my repo on github to found more tutorial about Vue3</a
      >
    </p>
    <button @click="getPosts">Click to Show Users from API</button>
  </div>

  <div class="table-container">
    <table>
      <thead>
        <tr>
          <th>#</th>
          <th>Name</th>
          <th>Username</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody>
        <tr class="tr-tbody" v-for="item in user" :key="item">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.username }}</td>
          <td>{{ item.email }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<!-- Option API -->

<!--
<script>
export default {
  data() {
    return {
      user: [],
    };
  },
  methods: {
    getPosts() {
      fetch("https://jsonplaceholder.typicode.com/users/")
        .then((res) => res.json())
        .then((data) => (this.user = data));

      const getTable = document.querySelector(".table-container");
      getTable.style.display = "block";
    },
  },
};
</script>
-->

<!-- Composition API -->

<!--
<script>
import { ref } from "vue";

export default {
  setup() {
    const user = ref([]);

    const getPosts = async () => {
      const res = await fetch("https://jsonplaceholder.typicode.com/users/");
      const finalRes = await res.json();
      user.value = finalRes;

      const getTable = document.querySelector(".table-container");
      getTable.style.display = "block";
    };

    return {
      user,
      getPosts,
    };
  },
};
</script>
-->

<!-- Script Setup -->

<script setup>
import { ref } from "vue";

const user = ref([]);

const getPosts = async () => {
  const res = await fetch("https://jsonplaceholder.typicode.com/users/");
  const finalRes = await res.json();
  user.value = finalRes;

  const getTable = document.querySelector(".table-container");
  getTable.style.display = "block";
};
</script>
