<template>
  <div>
    <!-- Form Input Nama -->
     <h1>Counter App</h1>
    <input v-model="nama" type="text" placeholder="Masukkan nama">
    <button @click="submitNama">Submit</button>

    <!-- Menampilkan pesan jika nama sudah diinput -->
    <p v-if="pesan" class="message">{{ pesan }}</p>

    <!-- Counter hanya muncul jika nama sudah dimasukkan -->
    <div v-if="pesan" class="counter">
      <span :class="counterClass">{{ counter }}</span>
      <button @click="decrement">-</button>
      <button @click="increment">+</button>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const nama = ref('')
const pesan = ref('')
const counter = ref(0)

// Fungsi untuk menampilkan pesan
const submitNama = () => {
  if (nama.value.trim() !== '') {
    pesan.value = `Halo, ${nama.value}!`
  }
}

// Fungsi untuk menambah/mengurangi counter
const increment = () => counter.value++
const decrement = () => counter.value--

// Menghitung kelas berdasarkan angka ganjil/genap
const counterClass = computed(() => ({
  'text-red': counter.value % 2 !== 0, // Merah jika ganjil
  'text-blue': counter.value % 2 === 0 // Biru jika genap
}))
</script>

<style scoped>

.message {
  font-size: 18px;
  margin-top: 10px;
}

.counter {
  margin-top: 20px;
  font-size: 24px;
}

.text-red {
  color: red;
}

.text-blue {
  color: blue;
}
</style>
