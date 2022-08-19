<template>
    <div id="barraizquierda">
        <div class="leftbar" :class="`${is_expanded && 'toggleleftbar'}`">

        <div class="togglebar" @click="toggleleftbar"><i class="fa-solid fa-angle-left"></i></div>

        <div class="logoshop">
            <center><div class="logoimg mt-3"></div></center>
        </div>

        <div class="sidebar">

            <div class="logotienda">
                <div class="logochange"><i class="fa-solid fa-pencil"></i></div>
            </div>

            <div class="links mt-4 mb-4">
                <ul class="navbar-nav">
                    <li class="nav-item text-orange mt-1 mb-1"><a href="#" class="nav-link home"><span>Home</span></a></li>
                    <li class="nav-item text-orange mt-1 mb-1"><a href="#" class="nav-link users"><span>Clientes</span></a></li>
                    <li class="nav-item text-orange mt-1 mb-1 selected"><a href="#" class="nav-link basket"><span>Ventas</span></a></li>
                    <li class="nav-item text-orange mt-1 mb-1"><a href="#" class="nav-link list"><span>Compras</span></a></li>
                    <li class="nav-item text-orange mt-1 mb-1"><a href="#" class="nav-link cash"><span>Caja</span></a></li>
                    <li class="nav-item text-orange mt-1 mb-1"><a href="#" class="nav-link stack"><span>Inventario</span></a></li>
                    <li class="nav-item text-orange mt-1 mb-1"><a href="#" class="nav-link tag"><span>Productos</span></a></li>
                    <li class="nav-item text-orange mt-1 mb-1"><a href="#" class="nav-link reportes"><span>Reportes</span></a></li>
                </ul>
            </div>

            <div class="buttonsbar">

                <button class="btn closebutton" style="margin-bottom: -3px;">Cerrar caja</button>
                <button class="btn closebutton">Salir</button>

            </div>

        </div>

    </div> 
    </div>
</template>

<script setup>
import { ref } from 'vue'

const is_expanded = ref(false)

const toggleleftbar = () => {
    is_expanded.value = !is_expanded.value
}
</script>

<script>
export default {
  name: 'LeftBar',
}
</script>
