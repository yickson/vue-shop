<template>
    <b-card
       :title="product.name"
       :img-src="product.picture"
       :img-alt="product.name"
       img-top
       style="max-width: 30rem;"
       class="mb-2" 
    >
    <p>Precio: {{ product.price }} $</p>
        <b-button
           block
           variant="warning"
           @click="$emit('addToCart', product)" 
        >
            Añadir al carrito
        </b-button>
    </b-card>
</template>

<script>
export default {
    props: {
        product:{
            type: Object,
            required: true,
        }
    }
}
</script>
