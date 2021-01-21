<template>
    <div class="read">
        <div class="nomer">
            <p> {{ayats.number.inSurah}}</p>
        </div>
     <div class="ayat">
         <p>{{ayats.text.arab}}</p>
         <p>{{ayats.translation.id}}</p>
     </div>
     <div class="play__sound" @click="play(ayats.audio.primary)">
         <b-icon icon="play-circle-fill"></b-icon>
     </div>
  </div>
</template>

<script>
export default {
    name:'Read',
    props:['ayats'],
    methods:{
        play(sound){
            if(sound){
                const audio = new Audio(sound);
                audio.load()
                audio.play()
            }
        },
    }
}
</script>

<style>
.read{
    display: flex;
    justify-content: space-between;

}
.play__sound{
    cursor: pointer;
    padding-left:10px;
}
.nomer{
    padding-right: 10px;
}
.ayat p{
    text-align: center;
}
.ayat p:nth-child(1){
        font-size: 20px;
}
</style>