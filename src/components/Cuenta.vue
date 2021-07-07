<template>
    <h3>Tipo de cuenta: {{tipo}}</h3>
    <h3>Tu Saldo actual: {{saldo}}</h3>
    <h3>Estado {{ estado ? 'Activa': 'Desactivada'}}</h3>
    <div v-for="(servicio, index) in servicios" :key="index">
      {{index +1}} - {{ servicio }}
    </div>
    <AccionSaldo texto="Aumentar Saldo" @accion="aumentar"/>
    <AccionSaldo texto="Disminuir Saldo" @accion="disminuir"/>
</template>

<script>
import AccionSaldo from './AccionSaldo.vue'
export default {
    name:'Cuenta',
    components: {
        AccionSaldo
    },
    data() {
        return {
            saldo: 1000,
            tipo: 'Debito',
            estado: true,
            servicios:['abono', 'transferencias', '']
        }
    },
    methods:{
        aumentar(){
            this.saldo = this.saldo + 100
        },
        disminuir(){
            this.saldo = this.saldo - 100
        }

    }

}
</script>

<style>

</style>