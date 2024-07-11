<template>
  <main>
    <table class="w-full">
      <thead>
        <tr>
          <th>名称</th>
          <th>大小</th>
          <th>修改日期</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in list" :key="item.name">
          <td>{{ item.name }}</td>
          <td>{{ item.size }}</td>
          <td>{{ item.mtime }}</td>
        </tr>
      </tbody>
    </table>
  </main>
</template>
<script setup lang="ts">
import { http } from '@/api/http'
import { ref } from 'vue'

interface Resource {
  name: string
  size: number
  mtime: string
}

const list = ref<Resource[]>([])

http.get('/').then((res) => {
  list.value = res.data
})
</script>
