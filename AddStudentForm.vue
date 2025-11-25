<template>
  <form class="form" @submit.prevent="submitForm">
    <input type="text" v-model="name" placeholder="Name" required />
    <input type="number" v-model="age" placeholder="Age" required />
    
    <button type="submit">Add Student</button>
    

    <!-- Отображение студентов после их добавления -->
    <div v-if="students.length > 0">
      <div v-for="(student, index) in students" :key="index" class="student">
        <p>Name: {{ student.name }}</p>
        <p>Age: {{ student.age }}</p>
      </div>
    </div>
  </form>
</template>

<script setup>
import { ref } from 'vue'

// Состояние для имени и возраста студента
const name = ref('')
const age = ref(null)

// Массив студентов
const students = ref([])

// Эмитируем событие для добавления студента
const emit = defineEmits(['add-student'])

// Функция для отправки формы
const submitForm = () => {
  if (name.value && age.value) {
    // Добавляем студента в список
    students.value.push({ name: name.value, age: age.value })
    // Очищаем поля формы
    name.value = ''
    age.value = null
  }
}

// Функция для обновления данных (вы можете настроить логику обновления по необходимости)
const update = () => {
  console.log('Name:', name.value)
  console.log('Age:', age.value)
}
</script>

<style scoped>
.form {
  margin: 20px 0;
  display: flex;
  flex-direction: column;
  gap: 10px;
  background: white;
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.07);
}

input {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 10px;
  font-size: 14px;
}

button {
  background: #10b981;
  color: white;
  border: none;
  border-radius: 8px;
  padding: 10px;
  cursor: pointer;
  font-weight: 600;
  transition: background 0.3s;
}

button:hover {
  background: #059669;
}

.student {
  background: #f1f1f1;
  padding: 10px;
  border-radius: 8px;
  margin-top: 10px;
}
</style>
