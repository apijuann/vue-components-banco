<template>
  <h3>Tipo de cuenta: {{tipocuenta}}</h3>
  <h3>Saldo: {{saldo}}</h3>
  <h4>Cuenta {{estado ? 'activa' : 'desactivada'}}</h4>
  <h4>Nuestros servicios: </h4>
  <div v-for="(servicio, index) in servicios" :key="index">
      {{index+1}} {{ servicio }}
  </div>
  <AccionSaldo  
    texto="Aumentar saldo" 
    @accion="aumentar"
    />
  <AccionSaldo 
    texto="Disminuir saldo"
     @accion="disminuir"
     :desactivar="desactivar"
   />
</template>

<script>
import AccionSaldo from './AccionSaldo'
export default {
    components: {
        AccionSaldo
    },
    data() {
        return {
            saldo: 1000,
            tipocuenta: 'Visa',
            estado: false,
            servicios: ['Pagos', 'Giros', 'Transferencias'],
            desactivar: false
        }
    },
    methods: {
        aumentar(){
            this.saldo += 100
            this.desactivar=false
        },
        disminuir(){
            if (this.saldo===0) {
                alert('Saldo cero')
                this.desactivar=true
                return
            } else {
                this.saldo -= 50
            }
        }
    }

}
</script>

<style>

</style>