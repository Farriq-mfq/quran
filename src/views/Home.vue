<template>
  <div class="home">
      <Navbar />
     <div class="container">
        <div class="row mt-5">
          <div class="col-lg-12 mb-5 opening">
           <div class="card">
              <h2>Welcome To<span class="badge">Quran App</span></h2>
              <p>Menambah keimanan anda </p>
              <p><router-link to="/surah" class="btn btn-info">Surah</router-link></p>
              <p>&copy; by Farriqmfq</p>
           </div>
          </div>
        </div>
     </div>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
export default {
  name: "Home",
  components:{
    Navbar,
  }
};
</script>
<style>
  .opening{
    line-height: 5vh;
    margin-top: 100px;
    height: 200px;
    border-radius: 10px;

  }
  .opening .card{
    border:none;
    margin-top: 30px;
    align-items: center;
  }
</style>