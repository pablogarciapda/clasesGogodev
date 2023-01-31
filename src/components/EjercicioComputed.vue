<template>
  <h2>Ejercicio calculo iva subtotal</h2>

  <div>
    <label for="">Subtotal</label>
    <input type="number" v-model="subtotal" />
    <h3>Total impuestos a pagar {{ totalIva }} =>({{ iva }}%)</h3>
    <h3>total factura {{ total }}</h3>
  </div>
</template>

<script lang="ts" setup>
  import { computed, Ref, ref } from 'vue'

  const iva = 21
  const subtotal: Ref<number> = ref(0)
  const totalIva = computed(() => (subtotal.value * iva) / 100)
  const total = computed(() => subtotal.value + totalIva.value)
</script>

<style scoped></style>
