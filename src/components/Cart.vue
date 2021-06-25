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
                <Item :cartNum="cartNum" v-if="cartNum > 0"></Item>
            </section>
            <footer class="modal-card-foot">
                <button class="button is-success">Save changes</button>
                <button class="button">Cancel</button>
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
    props: ['cartNum'],
    methods: {
       closeCart() {
           this.$emit('close')
       } 
    }
}
</script>

<style>

</style>