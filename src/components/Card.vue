<template>
    <div class="card" @click="redirect(surah.number)">
        <div class="card-body">
            <h5 class="card-title">
                <strong>{{surah.name.transliteration.id}}</strong>
                ({{surah.name.short}})
            </h5>
            <div class="card-text">
               {{surah.revelation.id}}
            </div>
            <div class="card-text">
              {{surah.numberOfVerses}} Ayat
            </div>
            <div class="card-text">
                {{surah.name.translation.id}}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'Card',
    props:['surah'],
    methods:{
        redirect(link){
            this.$router.push('surah/'+link+'')
        }
    }
}
</script>

<style>
.card{
    cursor: pointer;
}
</style>