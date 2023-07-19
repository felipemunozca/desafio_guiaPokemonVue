<template>

    <div class="data-container">
        <h2>Pokemon</h2>
        <img :src="dataPokemon.imagen" alt="">
        <p><strong>N° Pokedex Nacional:</strong> {{dataPokemon.id}}</p>
        <!-- <p><strong>Nombre:</strong> {{dataPokemon.nombre}}</p> -->
        <p><strong>Nombre:</strong> {{nombreFormateado}}</p>
        <div class="type-container">
            <p><strong>Tipo:</strong></p>
            <div v-for="(data, index) in listadoTipos" :key="index" class="">
                <img :src="require('@/assets/tipos/'+data+'.png')" alt="">
            </div>
        </div>
        <p><strong>Movimientos:</strong> {{listadoMovimientos}}</p>
        <p><strong>Habilidades:</strong> {{listadoHabilidades}}</p>
    </div>

</template>

<script>
export default {
    name: 'card-pokedex-comp',
    props: {
        dataPokemon: {
            type: Object,
            required: true,
        }
    },
    data: function(){
        return {}
    },
    computed: {
        nombreFormateado() {
            return this.dataPokemon.nombre.replace(/\b[a-z]/g,c=>c.toUpperCase());
        },
        listadoTipos() {
            return this.dataPokemon.tipo.map(tipo => {
                return tipo.type.name
            })
        },
        // imagen() {
            // return this.dataPokemon.imagen.front_default
            // return this.dataPokemon.imagen.other.home.front_default
        // }
        listadoMovimientos() {
            return this.dataPokemon.movimientos.map(movimiento => {
                return movimiento.move.name;
            }).join(', ')
        },
        listadoHabilidades() {
            return this.dataPokemon.habilidades.map(habilidad => {
                return habilidad.ability.name;

                // if (habilidad.is_hidden == false) {
                //     return habilidad.ability.name;
                // }
            }).join(', ');
        },

    },
    // methods: {}
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    .data-container {
        border: 1px solid lightgray;
        border-radius: 5px;
        margin: 10px;
        padding: 0 15px;
    }
    img {
        width: 150px;
    }
    .type-container {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
    }
    .type-container img {
        width: 110px;
    }
</style>