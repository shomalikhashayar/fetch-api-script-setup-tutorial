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

  <div class="content" v-for="item in user" :key="item">
    <table>
      <thead>
        <tr v-for="thead in theads" :key="thead">
          <th>{{thead.id}}</th>
          <th>{{thead.name}}</th>
          <th>{{thead.username}}</th>
          <th>{{thead.email}}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in user" :key="item">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.username }}</td>
          <td>{{ item.email }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: [],
      theads: [
        { id: "#" },
        { name: "name"},
        { username: "username"},
        { email: "email"},
      ],
    };
  },
  methods: {
    getPosts() {
      fetch("https://jsonplaceholder.typicode.com/users/")
        .then((res) => res.json())
        .then((data) => (this.user = data));
    },
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  font-family: sans-serif;
}
/* Hero Section */

.show-content {
  background: rgb(2, 0, 36);
  background: -moz-linear-gradient(
    66deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(52, 73, 94, 1) 0%,
    rgba(52, 73, 94, 1) 0%,
    rgba(65, 184, 179, 1) 100%
  );
  background: -webkit-linear-gradient(
    66deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(52, 73, 94, 1) 0%,
    rgba(52, 73, 94, 1) 0%,
    rgba(65, 184, 179, 1) 100%
  );
  background: linear-gradient(
    66deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(52, 73, 94, 1) 0%,
    rgba(52, 73, 94, 1) 0%,
    rgba(65, 184, 179, 1) 100%
  );
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr="#020024",endColorstr="#41b8b3",GradientType=1);
  height: 700px;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.show-content h2 {
  font-weight: bold;
  font-size: 2.5rem;
  text-transform: capitalize;
  max-width: 600px;
  text-align: center;
  line-height: 50px;
  margin-bottom: 50px;
}

.show-content a {
  text-decoration: none;
  color: rgb(189, 255, 246);
  font-size: 1.7rem;
}

.show-content p {
  width: 450px;
  text-align: center;
  text-transform: capitalize;
  line-height: 35px;
  margin-bottom: 50px;
}

.show-content button {
  background-color: transparent;
  border: 2px solid white;
  border-radius: 9px;
  padding: 15px 40px;
  font-size: 22px;
  font-weight: bold;
  color: white;
  cursor: pointer;
}

.show-content button:hover {
  background-color: #34495e;
}

/* Table */

table {
  width: 100%;
  border-collapse: collapse;
}

td {
  border: 1px solid;
}

th{
  background-color: antiquewhite;
  border: none;
}

</style>
