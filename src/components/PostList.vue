<template>
  <div class="container">
    <PostDetail
      v-for="elem in infoPost"
      :key="elem.title"
      :title="elem.title"
      :description="elem.description"
      @alerta="ShowAlert"
    />
  </div>
</template>

<script setup lang="ts">
  import PostDetail from './PostDetail.vue'

  interface IPost {
    title: string
    description: string
  }

  let infoPost: Array<IPost> = [
    { title: 'post 1', description: 'contenido post 1' },
    { title: 'post 2', description: 'contenido post 2' },
    { title: 'post 3', description: 'contenido post 3' },
    { title: 'post 4', description: 'contenido post 4' },
    { title: 'post 5', description: 'contenido post 5' },
  ]
  function ShowAlert(msg: string) {
    alert(msg)
  }
</script>

<style scoped>
  .container {
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    justify-content: space-around;
  }
</style>
