<template>
  <div class="list">
    <transition-group name="list" tag="ul" class="cards">
      <li v-for="student in students" :key="student.id">
        
        <!-- Student card -->
        <student-card 
          :student="student"
          @remove="remove(student.id)"
        />

       

      </li>
    </transition-group>
      <!--
        TASK:
        1. Display all students in a list using the StudentCard component to display each student.
        2. Use the transition-group component to animate the list.
        3. Catch the 'remove' event and emit 'remove-student' from this component with the student's id.
    -->
  </div>
</template>

<script setup>
import StudentCard from './StudentCard.vue'

defineProps({
  students: Array
})

const emit = defineEmits(['remove-student'])

const remove = (id) => emit('remove-student', id)
</script>

<style scoped>
.list-enter-active,
.list-leave-active {
  transition: all 0.4s ease;
}

.list-enter-from {
  opacity: 0;
  transform: translateY(10px);
}

.list-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

.list {
  margin-top: 30px;
}
.cards {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.4s ease;
}
.fade-enter-from {
  opacity: 0;
  transform: translateY(10px);
}
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
