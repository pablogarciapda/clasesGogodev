<script setup lang="ts">
  import { defineProps, defineEmits, Ref, ref } from 'vue'
  const props = defineProps({
    title: {
      type: String,
      required: true,
    },
    description: {
      description: String,
      default: 'texto por defecto',
    },
  })
  const emit = defineEmits(['alerta'])
  const message: Ref<string> = ref('')
  const handleClick = () => {
    emit('alerta', message.value)
  }
  // export default defineComponent({
  //   name: 'PostDetal',
  //   props: {
  //     title: {
  //       type: String,
  //       requered: true,
  //     },
  //     description: {
  //       type: String,
  //       default: 'Texto por defecto del post',
  //     },
  //   },
  //   emits: ['alerta'],
  //   setup(props, { emit }) {
  //     const message: Ref<string> = ref('')
  //     const handleClick = () => {
  //       emit('alerta', message.value)
  //     }
  //     return { props, handleClick, message }
  //   },
  // })
</script>

<template>
  <div class="post">
    <h3>{{ props.title }}</h3>
    <p>
      {{ props.description }}
    </p>
    <input type="text" v-model="message" />
    <button @click="handleClick">di hola</button>
  </div>
</template>

<style scoped>
  .post {
    width: 250px;
    height: 125px;
    background-color: aquamarine;
    border-radius: 10px;
    padding: 10px;
    margin: 6px;
  }
</style>
