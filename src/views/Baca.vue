<template>
  <div class="container">
      <div class="row">
        <Top />
      <div class="col-md-12">
        <div class="card">
          <div class="card-header shadow">
           <div class="header">
                <p>{{surahDetails.revelation.arab}}</p>
              <h4>{{surahDetails.name.transliteration.id}} ({{surahDetails.name.short}})
                <span>({{surahDetails.name.translation.id}})</span>
              </h4>
              <p>{{surahDetails.numberOfVerses}} Ayat</p>
           </div>
           <div class="back">
             <router-link to="/surah" class="btn"><b-icon icon="arrow-return-left"></b-icon></router-link>
           </div>
          </div>
          <div class="card-body" v-if="loading">
              <b-skeleton v-for="fake in fakes" :key="fake.id" animation="wave" width="100%" class="skeleton"></b-skeleton>
          </div>
          <div class="card-body" v-for="ayats in ayat" :key="ayats.id">
            <Read :ayats = ayats />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Top from '@/components/Top.vue'
import Read from '@/components/Read.vue'
import axios from 'axios';
export default {
    name:'Baca',
    components:{
      Read,
      Top,
    },
    data(){
      return {
        surahDetails:[],
        ayat:[],
        fakes:10,
        loading:true,
      }
    },
    methods:{
      Detail(data){
        this.surahDetails = data;
      },
      Detailsayat(data){
        this.ayat = data
      },
    },
    mounted(){
     axios.get('https://api.quran.sutanlab.id/surah/'+this.$route.params.id).then(res=>{
      this.Detail(res.data.data)
      setTimeout(() => {
        this.loading = false;
        this.Detailsayat(res.data.data.verses);
      }, 3000)
      
      
     }).catch(err=>{
       console.log(err)
     })
    }
}
</script>

<style>
  .card{
    margin-top: 15px;
    cursor:auto;
  }
  .header{
    background: transparent;
    display: flex;
    align-items: center;
    justify-content: space-around;
  }
  .header p:nth-child(1){
    height: 70px;
    width: 70px;
    align-items: center;
    text-align: center;
    padding-top: 20px;
    border-radius: 50%;
    margin-top: 5px;
    background: rgb(189, 255, 183);
    font-weight: 600;
  }
  .header p:nth-child(3){
    height: 70px;
    width: 70px;
    align-items: center;
    text-align: center;
    padding-top: 17px;
    border-radius: 50%;
    margin-top: 5px;
    background: rgb(189, 255, 183);
    font-weight: 600;
  }
  span{
    display: block;
    text-align: center;
    font-size: 16px;
    margin-top: 4px;
  }
  @media screen and (max-width:567px){
    h4{
      font-size: 17px !important;
    }
  }
  .skeleton{
    margin: auto;
  }
</style>