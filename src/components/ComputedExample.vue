<template>
  <div>
    <input type="text" v-model="msg" />
    <h3>{{ msg }}</h3>
    <h3>{{ reverse }}</h3>
  </div>
</template>

<script lang="ts" setup>
  import { ref, Ref, computed } from 'vue'
  let msg: Ref<string> = ref('')

  const reverse: Ref<string> = computed(() =>
    msg.value.split('').reverse().join('')
  )
</script>

<style scoped></style>
