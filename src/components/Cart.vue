<template>
    <div v-if="cart.length">
        <b-table striped hover :items="cart" :fields="fields">
            <template slot="actions" slot-scope="cell">
                <b-button
                    size="sm"
                    variant="danger"
                    @click.stop="removeProductFromCart(cell.item)"
                >
                    Eliminar
                </b-button>
            </template>
        </b-table>
        <b-alert show variant="success" class="text-center">
            Coste total: {{ totalCost | rounded }}$
        </b-alert>
    </div>
    <b-alert v-else show variant="info">
        No hay productos en el carrito
    </b-alert>
</template>

<script>
import {mapGetters, mapMutations, mapState} from 'vuex'
export default {
    data(){
        return{
            fields: ['name', 'qty', 'price', 'actions']
        }
    },
    computed: {
        ...mapState('cart', ['cart']),
        ...mapGetters('cart', ['totalCost']),
    },
    methods: {
        ...mapMutations('cart', ['removeProductFromCart'])
    },
    filters: {
        rounded: function (value) {
            if (!value) return ''
            value = value.toFixed(2)
            return value
        }
    }
}
</script>
