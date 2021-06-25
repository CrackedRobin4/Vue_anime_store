<template>
    <div class="modal is-active">
        <div class="modal-background" @click.self="closeAdded"></div>
        <div class="modal-card">
            <header class="modal-card-head">
                <p class="modal-card-title">Notification about Adding item</p>
                <button class="delete" aria-label="close" @click="closeAdded"></button>
            </header>
            <section class="modal-card-body">
                <h1>You succesfully added item to the shopping cart</h1>
            </section>
            <footer class="modal-card-foot">
            </footer>
        </div>
        </div>
</template>

<script>
export default {
    methods: {
       closeAdded() {
           this.$emit('closeAdded')
       } 
    }
}
</script>

<style>

</style>