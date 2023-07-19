<template>
    <div class="search-container">
        <h2>Buscador</h2>
        <form class="">
            <label for="">Id o Nombre:</label>
            <input v-model="pokemonBuscado" placeholder="escriba un pokemon">
            <button @click.prevent="buscarPokemon">Buscar</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'buscador-comp',
    // props: {},
    data: function(){
        return {
            pokemonBuscado: 'pikachu',
        }
    },
    // computed: {},
    methods: {
        buscarPokemon() {
            if (this.pokemonBuscado == '') {
                alert('El nombre o id no puede ir vació');
                return;
            }

            this.$emit('buscarPokemon', this.pokemonBuscado);
        }
    },
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    .search-container {
        border: 1px solid lightgray;
        border-radius: 5px;
        margin: 10px;
        max-height: 150px;
    }
    /* .search-container h2 {
        background-color: lightgray;
    } */
    .search-container form {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
        padding-left: 10px;
    }
    .search-container input {
        padding: 8px;
    }
    .search-container button {
        background-color: #03C988;
        padding: 8px;
        color: white;
        cursor: pointer;
        border: none;
        border-radius: 4px;
        width: 80px;
    }
    .search-container button:hover {
        background-color: #5F8D4E;
    }
</style>