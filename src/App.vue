<script setup>
    import { ref, reactive, onMounted } from 'vue'

    import Header from './components/Header.vue'

    import Guitarra from './components/Guitarra.vue'

    import Footer from './components/Footer.vue'

    import { db } from'./data/guitars'
    //uso de reactive
    // const state = reactive({
    //     guitarras: db
    // })
    // console.log(state.guitarras)
    
    // uso de ref
    const guitarras = ref([])
    const carrito = ref([])

    onMounted(()=>{
        console.log('Componente listo')
        guitarras.value = db
    })

    const agregarCarrito = (guitarra) => {
        guitarra.cantidad = 1
        carrito.value.push(guitarra)
    }

    

</script>

<template>
    <Header 
    v-bind:carrito="carrito"
    />
    <main class="container-xl mt-5">
        <h2 class="text-center">Nuestra Colección</h2>

        <div class="row mt-5">
            <Guitarra
                v-for="guitarra in guitarras"
                v-bind:guitarra="guitarra"
                @agregar-carrito="agregarCarrito"
            />
        </div>
    </main>


    <Footer/>
</template>

<style>

</style>