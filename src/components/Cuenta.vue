<template>
    <h3>Tipo de cuenta: {{tipo}}</h3>
    <h3 v-if="saldo > 200 ">Tu Saldo actual: {{saldo}}</h3>
    <h3 v-else style="color:red">Tu Saldo actual: {{saldo}} </h3>
    <h3>Estado {{ estado ? 'Activa': 'Desactivada'}}</h3>

    <div v-for="(servicio, index) in servicios" :key="index">
      {{index +1}} - {{ servicio }}
    </div>

    <AccionSaldo texto="Aumentar Saldo" @accion="aumentar" />
    <AccionSaldo texto="Disminuir Saldo" @accion="disminuir" :disabled="desactivar"/>
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
            servicios:['abono', 'transferencias', ''],
            desactivar: false
        }
    },
    methods:{
        aumentar(){
            this.saldo = this.saldo + 100
             this.desactivar= false;
        },
        disminuir(){
            if(this.saldo === 0){
                this.desactivar= true;
                return
            }
            this.saldo = this.saldo - 100
        }

    }

}
</script>

<style>

</style>