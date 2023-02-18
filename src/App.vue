<template>
  <div class="show-content" id="show-content">
    <h2>
      in this tutorial i wanna try to teach you how fetch api with vue 3 script
      setup
    </h2>
    <p>
      <a href="https:github.com/shomalikhashayar"
        >check my repo on github to found more tutorial about Vue3</a
      >
    </p>
    <button @click="getPosts" class="click-to-show-content">
      <a href="#body">Click to Show Users from API</a>
    </button>
    <button class="go-to-table-button">
      <svg
        style="color: white"
        xmlns="http://www.w3.org/2000/svg"
        width="20"
        height="20"
        fill="currentColor"
        class="bi bi-arrow-down"
        viewBox="0 0 16 16"
      >
        <path
          fill-rule="evenodd"
          d="M8 1a.5.5 0 0 1 .5.5v11.793l3.146-3.147a.5.5 0 0 1 .708.708l-4 4a.5.5 0 0 1-.708 0l-4-4a.5.5 0 0 1 .708-.708L7.5 13.293V1.5A.5.5 0 0 1 8 1z"
          fill="white"
        ></path></svg
      ><a href="#body"><span>Go to Table</span></a>
    </button>
  </div>

  <div class="table-container">
    <table>
      <thead id="header">
        <tr>
          <th>#</th>
          <th>Name</th>
          <th>Username</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody id="body">
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

      const goToTableButton = document.querySelector(".go-to-table-button");
      goToTableButton.style.display = "block";
    },
  },
};
</script>

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
<!--
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
-->
