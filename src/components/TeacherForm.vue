<script setup lang="ts">
  import { Ref, ref } from 'vue'

  interface Iteacher {
    teacherName: string
    teacherApellidos: string
    dni: string
    materias: Array<string>
    documentacion: boolean
  }

  let teacher: Ref<Iteacher> = ref({
    teacherName: '',
    teacherApellidos: '',
    dni: '',
    materias: [],
    documentacion: false,
  })
  let materia: Ref<string> = ref('')
  let teachers: Ref<Array<Iteacher>> = ref([])
  let inputMateria = ref()

  const handleMaterias = () => {
    teacher.value.materias.push(materia.value)
    materia.value = ''
    inputMateria.value.focus()
  }
  const handleAgregar = () => {
    teachers.value.push(teacher.value)
    teacher.value = {
      teacherName: '',
      teacherApellidos: '',
      dni: '',
      materias: [],
      documentacion: false,
    }
  }
</script>

<template>
  <section>
    <h3>Añadir profesor</h3>
    <div>
      <label for="nombre">Nombre:</label>
      <input type="text" v-model="teacher.teacherName" />
    </div>
    <div>
      <label for="apellidos">Apellidos:</label>
      <input type="text" v-model="teacher.teacherApellidos" />
    </div>
    <div>
      <label for="dni">DNI / NIF:</label>
      <input type="text" v-model="teacher.dni" />
    </div>
    <div>
      <label for="materias">Materias:</label>
      <input
        ref="inputMateria"
        type="text"
        v-model="materia"
        @keyup.enter="handleMaterias"
      />
      <button @click="handleMaterias">añadir</button>
      <div v-if="teacher.materias.length != 0">
        <ul>
          <li v-for="(elem, index) in teacher.materias" :key="index">
            {{ elem }}
          </li>
        </ul>
      </div>
    </div>
    <input type="checkbox" v-model="teacher.documentacion" />Documentacion
    entregada
    <button @click="handleAgregar">Agregar</button>
  </section>

  <section>
    <h3>Listado de profesores</h3>
    <table>
      <tr>
        <th>Nombre</th>
        <th>Apellidos</th>
        <th>DNI</th>
        <th>Materias</th>
        <th>Documentacion</th>
      </tr>
      <tr v-for="elem in teachers" :key="elem.dni">
        <th>{{ elem.teacherName }}</th>
        <th>{{ elem.teacherApellidos }}</th>
        <th>{{ elem.dni }}</th>
        <th>
          <ul>
            <li v-for="(item, index) in elem.materias" :key="index">
              {{ item }}
            </li>
          </ul>
        </th>
        <th v-if="elem.documentacion">Entregada</th>
        <th v-else>No entregada</th>
      </tr>
    </table>
  </section>
</template>

<style scoped></style>
