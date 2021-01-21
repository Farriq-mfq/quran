<template>
  <div>
      <Navbar />
        <div class="container">
            <form>
                <input type="text" class="form-control" placeholder="Cari surat" v-model="keyword">
            </form>
            <div class="row mt-5">
                <div class="col-md-3 mb-3" v-for="surah in filter" :key='surah.id' >
                    <Card :surah = surah />
                </div>
               <template v-if="loading">
                    <div class="col-md-3 mb-3"  v-for="fake in fakes" :key='fake.id'>
                        <b-card>
                            <b-skeleton animation="wave" width="85%"></b-skeleton>
                            <b-skeleton animation="wave" width="70%"></b-skeleton>
                            <b-skeleton animation="wave" width="55%"></b-skeleton>
                            <b-skeleton animation="wave" width="70%"></b-skeleton>
                        </b-card>
                    </div>
               </template>
            </div>
        </div>``
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
import Card from '@/components/Card.vue'
import axios from 'axios'
export default {
    name:'Surah',
    components:{
        Navbar,
        Card
    },
    data(){
        return{
            surat:[],
            keyword:'',
            fakes:114,
            loading:true,
        }
    },
    methods:{
        setSurah(data){
            this.surat = data
        }
    },
    computed:{
        filter(){
            return this.surat.filter((surah)=>{
                return surah.name.transliteration.id.toLowerCase().includes(this.keyword.toLowerCase());
            })
        }
    },
    mounted(){
        axios.get('https://api.quran.sutanlab.id/surah').then(response=>{
            setTimeout(() => {
                this.loading = false;
                this.setSurah(response.data.data);
            }, 3000)
            
        }).catch(err=>{
            console.log(err)
        })
    },
   
}
</script>

<style>

</style>