<template>
    <div>
        <h1>Galeria de fotos</h1>
        <router-link :to="{name:'Fotos',params:{id:item}}" 
        v-for="(item,index) of fotosArr" :key="index">
            <button>foto {{item}}</button>
        </router-link>

        <Foto/>
          <b-button @click="home" class="mx-1">Home</b-button>
          <b-button @click="anterior" class="mx-1">Anterior</b-button>
          <b-button @click="siguiente" class="mx-1">Siguiente</b-button>

    </div>
</template>

<script>
import Foto from '@/components/Fotografia.vue'

export default {
    components:{
        Foto
    },
    data(){
        return{
            fotosArr: [1,2,3,4,5],
            imageUrl: 'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/',
            apiUrl: 'https://pokeapi.co/api/v2/pokemon/'
        }
    },
    methods:{
        home(){
            this.$router.push('/')
        },
        anterior(){
            this.$router.go(-1)
        },
        siguiente(){
            this.$router.go(1)
        }
    }
}
</script>