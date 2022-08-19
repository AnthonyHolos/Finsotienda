<template>
    <div id="barraderecha">
        <div class="rightbar" :class="`${is_expanded && 'togglerightbar'}`">
        
        <div class="togglenewbar" @click="togglerightbar"><i class="fa-solid fa-angle-right"></i></div>

        <div class="supbar text-orange">
            <div class="d-flex justify-content-center mb-4">
                <div class="titlecart mt-4">Carrito de<br>Compras</div>
            </div>
            <center><div class="dashedline"></div></center>
            <div class="totalprice">
                <span>Total</span><br>
                <span class="price">$0</span>
            </div>
            <center><div class="dashedline"></div></center>
        </div>

        <div class="productsbar">
            <div class="productselecteds">

                <div class="productselect d-flex mb-4" v-for="(cursoCesta, index) in cesta" :key="index">
                    <span class="nameproduct">{{cursoCesta.curso.name}} <br><b class="priceandcount">${{cursoCesta.curso.precio}} X{{cursoCesta.cant}}</b></span>
                    <div class="deleteproduct text-danger"><i class="fa-solid fa-trash"></i></div>
                </div>
                
            </div>
        </div>

        <div class="infbar">
            <input type="number" class="inputfilter w-100 mb-3" placeholder="Celular">
            <button class="btn inactivebtn" style="margin: 0!important; ">Vender</button>
        </div>

        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const is_expanded = ref(false)

const togglerightbar = () => {
    is_expanded.value = !is_expanded.value
}
</script>

<script>
    export default {
        name: 'RightBar',
        methods: {
            agregarCesta: function (curso) {
            var prodExistente;
            var exitente = this.cesta.filter(function (item, index) {
                if (item.curso.id == Number(curso.id)) {
                prodExistente = index;
                return true;
                } else {
                return false;
                }
            });

            if (exitente.length) {
                this.cesta[prodExistente].cant++;
            } else {
                this.cesta.push({ curso: curso, cant: 1 });
            }
            },
        }
    }
</script>