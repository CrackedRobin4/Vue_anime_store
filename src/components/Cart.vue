<template>
    <div class="modal is-active">
        <div class="modal-background" @click.self="closeCart"></div>
        <div class="modal-card">
            <header class="modal-card-head">
                <p class="modal-card-title">Shopping Cart</p>
                <button class="delete" aria-label="close" @click="closeCart"></button>
            </header>
            <section class="modal-card-body">
                <p v-if="cartNum == 0"> Sorry, your Shopping Cart is empty</p>
                <Item @remove="removeFromCart" :cartNum="cartNum" :price="price" v-if="cartNum > 0"></Item>
            </section>
            <footer class="modal-card-foot">
                
            </footer>
        </div>
    </div>
</template>

<script>
import Item from './Item.vue'
export default {
    components: {
        Item
    },
    props: ['cartNum', 'price'],
    methods: {
       closeCart() {
           this.$emit('close')
       },
       removeFromCart(){
           this.$emit('remove')
       }
    }
}
</script>

<style>

</style>