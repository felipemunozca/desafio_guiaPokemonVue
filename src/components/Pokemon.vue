<template>
    <div class="">
        <h1>Guía Pokemon</h1>
        <div class="principal-container">
            <form-buscador @buscarPokemon='asignarNombrePokemon'/>
            <card-pokedex :dataPokemon='infoPokemon'/>
        </div>
        
    </div>
</template>

<script>
import Buscador from '@/components/Buscador.vue';
import CardPokedex from '@/components/CardPokedex.vue';

export default {
    name: 'pokemon-comp',
    // props: {},
    data: function(){
        return {
            nombrePokemon: 'pikachu',
            infoPokemon: {
                id: '',
                nombre: '',
                //tipo: '',
                tipo: [],
                imagen: '',
                movimientos: [],
                habilidades: []
            },
        }
    },
    // computed: {},
    methods: {
        async obtenerPokemon() {
            try{
                let consultaAPI = await fetch(`https://pokeapi.co/api/v2/pokemon/${this.nombrePokemon}`);
                //let consultaAPI = await fetch(`https://pokeapi.co/api/v2/pokemon/bulbasaur`);
                let respuesta = await consultaAPI.json();
                this.infoPokemon.id = respuesta.id;
                this.infoPokemon.nombre = respuesta.name;
                this.infoPokemon.tipo = respuesta.types;
                this.infoPokemon.imagen = respuesta.sprites.other['official-artwork'].front_default;
                this.infoPokemon.movimientos = respuesta.moves;
                this.infoPokemon.habilidades = respuesta.abilities;

                /* console.log(this.infoPokemon) */
                /* console.log(this.infoPokemon.id) */
                /* console.log(this.infoPokemon.nombre) */
                /* console.log(this.infoPokemon.tipo) */
                /* console.log(this.infoPokemon.imagen) */
                /* console.log(this.infoPokemon.movimientos) */
                /* console.log(this.infoPokemon.habilidades) */
            }
            catch(error){
                alert('El id o nombre ingresado no es correcto.\nPor favor escribirlo nuevamente.');
                console.log(error);
            }
        },
        asignarNombrePokemon(nombre){
            this.nombrePokemon = nombre;
        },
    },
    watch: {
        nombrePokemon(value) {
            if (value != '') {
                this.obtenerPokemon();
                console.log(value)
            }
        },
    },
    components: {
        'form-buscador': Buscador,
        'card-pokedex':CardPokedex,
    },
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    created() {
        this.obtenerPokemon();
    }
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    .principal-container{
        width: 90%;
        margin: 0 auto;
        display: grid;
        grid-template-columns: 1fr 1fr;
    }
</style>