<template>
  <div>Hola mundo</div>
</template>

<!-- OPTION API -->
<!-- 
<script lang="ts">
  import { defineComponent } from 'vue'

  export default defineComponent({
    name: 'CycleOption',
    data(): void {
      const mensaje = ''
    },

    methods: {},
    created() {
      console.log('created')
    },
    mounted() {
      console.log('monted')
    },
    updated() {
      console.log('updated')
    },
  })
</script> -->

<!-- COMPOSITION API -->

<script lang="ts" setup>
  import { onMounted, onUpdated } from 'vue'

  onMounted(() => {
    console.log('onMounted')
  })

  onUpdated(() => {
    console.log('onUpdated')
  })
</script>

<style scoped></style>
