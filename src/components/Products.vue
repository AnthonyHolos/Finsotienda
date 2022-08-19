<template>
    <div id="cataproductos">
        <div class="productssection mt-4">
            <div class="container">
                <div class="row">



                    <div v-for="currency in info"
                    :key="currency.id"
                    class="col-md-3 element mb-4">
                        <div class="product">
                            <div class="imgproduct" v-bind:style="{ 'background-image': 'url(' + currency.imagen + ')' }">
                            </div>
                            <span>{{ currency.nombre }}</span><br>
                            <small style="font-weight: bold;">$ {{ currency.precio }} </small>
                        </div>
                        <div class="mt-4 menubtn d-flex">
                            <div class="restproduct">
                                <i class="fa-solid fa-minus"></i>
                            </div>
                            <input type="number" class="cantidad" name="" id="" placeholder="0">
                            <div class="sumproduct" v-on:click="agregarCesta(curso)">
                                <i class="fa-solid fa-plus"></i>
                            </div>
                        </div>
                    </div>
                
                </div>
            </div>
        </div>
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
import datos from '../assets/productos.json'
import RightBar from './RightBar.vue'

export default {
    name: 'products',
    components: {
    RightBar
},
    computed: {
        info() {
            return datos.map((currency) => {
                return currency;
            })
        }
    },
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