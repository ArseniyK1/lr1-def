<template>
  <div class="vue">
    <main>
      <div class="inf">
        <h2 style="margin-top: 15px; text-align: center">
          <nuxt-link to="/vigener"> Метод Виженера</nuxt-link>
        </h2>
        <h2 style="margin-top: 15px; text-align: center">
          <nuxt-link to="/gamma">Гаммирование</nuxt-link>
        </h2>
      </div>
    </main>
  </div>
</template>

<style scoped>
.vue {
  font-family: 'Courier New', Courier, monospace;
  min-height: 100vh;
  color: whitesmoke;
  text-align: left;
}

nuxt-link,
h2 {
  text-decoration: none;
}

.container {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  flex-direction: column;
  align-items: center;
}

input {
  border-radius: 10px;
  width: 500px;
  margin-top: 20px;
  text-align: left;
}

h2 {
  text-decoration: none;
}

h5 {
  margin-top: 10px !important;
  margin: 10px auto;
}

.title {
  text-align: center;
  font-family: 'Courier New', Courier, monospace;
}

.inf {
  width: 400px;
  height: 400px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 0 auto;
  margin-top: 10%;
  border: 4px solid black;
  border-radius: 15px;
  color: white !important;
  background: #e9b872 !important;
}

a {
  color: white !important;
}
</style>
<style>
body {
  background-color: #bbc7ce;
}
</style>
