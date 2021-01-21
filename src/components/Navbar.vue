<template>
  <nav class="navbar navbar-expand-lg navbar-light">
  <div class="container">
    <router-link to="/" class="navbar-brand m-auto">Home</router-link>
    <ul class="navbar-nav m-auto">
        <li class="nav-item">
            <router-link class="nav-link active" to="/surah">Surah</router-link>
        </li>
    </ul>
  </div>
</nav>
</template>

<script>
export default {
    name:'Navbar'
}
</script>

<style>

</style>