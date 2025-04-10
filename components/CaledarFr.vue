<script setup>
import { ref, computed, watch } from 'vue';

const daysOfWeek = ['Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб', 'Вс'];
const months = [
  'Январь', 'Февраль', 'Март', 'Апрель',
  'Май', 'Июнь', 'Июль', 'Август',
  'Сентябрь', 'Октябрь', 'Ноябрь', 'Декабрь'
];

const currentDate = ref(new Date());
const selectedDate = ref(null);
const selectedMonth = ref(new Date().getMonth());
const selectedYear = ref(new Date().getFullYear());

const currentWeek = computed(() => {
  const startDate = new Date(currentDate.value);
  startDate.setDate(startDate.getDate() - startDate.getDay() + 1);
  
  return Array.from({ length: 7 }, (_, i) => {
    const date = new Date(startDate);
    date.setDate(startDate.getDate() + i);
    
    return {
      date: date,
      number: date.getDate(),
      isCurrentMonth: date.getMonth() === currentDate.value.getMonth()
    };
  });
});

const isSelected = (date) => {
  return selectedDate.value?.toDateString() === date.toDateString();
};

const selectDate = (date) => {
  selectedDate.value = date;
};

const scrollWeek = (weeks) => {
  const newDate = new Date(currentDate.value);
  newDate.setDate(newDate.getDate() + weeks * 7);
  currentDate.value = newDate;
  updateControls();
};

const updateControls = () => {
  selectedMonth.value = currentDate.value.getMonth();
  selectedYear.value = currentDate.value.getFullYear();
};

const updateCalendar = () => {
  currentDate.value = new Date(
    selectedYear.value,
    selectedMonth.value,
    currentDate.value.getDate()
  );
};

watch([selectedMonth, selectedYear], updateCalendar);
</script>

<template>
    <div class="calendar-container">

      <div class="controls">
        <select v-model="selectedMonth" @change="updateCalendar">
          <option v-for="(month, index) in months" :value="index" :key="month">
            {{ month }}
          </option>
        </select>
        <input 
          type="number" 
          v-model="selectedYear" 
          @change="updateCalendar"
          min="1900" 
          max="525252"
        >
      </div>
  
      <div class="week-header">
        <div 
          v-for="day in daysOfWeek" 
          :key="day"
          class="day-label"
        >
          {{ day }}
        </div>
      </div>

      <div class="week-grid">
        <div
          v-for="day in currentWeek"
          :key="day.date.toString()"
          class="day-cell"
          :class="{
            selected: isSelected(day.date),
            'different-month': !day.isCurrentMonth
          }"
          @click="selectDate(day.date)"
        >
          {{ day.number }}
        </div>
      </div>

      <div class="navigation">
        <button @click="scrollWeek(-1)">← Предыдущая</button>
        <button @click="scrollWeek(1)">Следующая →</button>
      </div>
    </div>
  </template>
  
<div></div>
  
  <style scoped>
  .calendar-container {
    max-width: 600px;
    margin: 20px auto;
    font-family: 'Arial', sans-serif;
  }
  
  .controls {
    display: flex;
    gap: 15px;
    margin-bottom: 20px;
  }
  
  select, input {
    padding: 8px 12px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 16px;
  }
  
  .week-header {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 5px;
    margin-bottom: 10px;
  }
  
  .day-label {
    text-align: center;
    padding: 10px;
    font-weight: bold;
    color: #666;
  }
  
  .week-grid {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 5px;
  }
  
  .day-cell {
    padding: 15px;
    text-align: center;
    border: 1px solid #eee;
    cursor: pointer;
    transition: all 0.2s;
  }
  
  .day-cell:hover {
    background: #f8f8f8;
  }
  
  .selected {
    background: #ff4444;
    color: white;
    border-color: #ff4444;
  }
  
  .different-month {
    color: #999;
    background: #f5f5f5;
  }
  
  .navigation {
    margin-top: 20px;
    display: flex;
    justify-content: space-between;
    gap: 10px;
  }
  
  button {
    padding: 8px 20px;
    background: #FF3F3F;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background 0.2s;
  }
  
  button:hover {
    background: #FF3F3F;
  }
  .calendar-container {
  max-width: 600px;
  margin: 2rem auto;
  padding: 1.5rem;
  background: #ffffff;
  border-radius: 16px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
  font-family: 'Segoe UI', system-ui, sans-serif;
}

.controls {
  display: flex;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

select {
  padding: 0.6rem 1rem;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  font-size: 1rem;
  background: #f8f9fa;
  transition: all 0.2s ease;
  appearance: none;
  background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='currentColor' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3e%3cpolyline points='6 9 12 15 18 9'%3e%3c/polyline%3e%3c/svg%3e");
  background-repeat: no-repeat;
  background-position: right 0.8rem center;
  background-size: 1em;
}

select:focus {
  outline: none;
  border-color: #FF3F3F;
  box-shadow: 0 0 0 3px rgba(77, 144, 254, 0.15);
}

input[type="number"] {
  padding: 0.6rem 1rem;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  font-size: 1rem;
  background: #f8f9fa;
  transition: all 0.2s ease;
}

input[type="number"]:focus {
  outline: none;
  border-color: #FF3F3F;
  box-shadow: 0 0 0 3px rgba(77, 144, 254, 0.15);
}

.week-header {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 0.25rem;
  margin-bottom: 0.5rem;
}

.day-label {
  text-align: center;
  padding: 0.75rem;
  font-weight: 600;
  color: #6b7280;
  font-size: 0.9em;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.week-grid {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 0.25rem;
}

.day-cell {
  padding: 1rem;
  text-align: center;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.2s ease;
  font-weight: 500;
  background: #ffffff;
  border: 2px solid transparent;
  color: #1f2937;
}

.day-cell:hover {
  background: #f3f4f6;
  transform: translateY(-1px);
}

.day-cell.selected {
  background: #FF3F3F;
  color: white;
  border-color: #FF3F3F;
  box-shadow: 0 4px 6px -1px rgba(59, 130, 246, 0.3);
}

.day-cell.different-month {
  color: #9ca3af;
  background: #f8f9fa;
}

.navigation {
  margin-top: 1.5rem;
  display: flex;
  justify-content: space-between;
  gap: 0.5rem;
}

button {
  padding: 0.6rem 1.25rem;
  background: #FF3F3F;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.2s ease;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

button:hover {
  background: #FF3F3F;
  transform: translateY(-1px);
  box-shadow: 0 4px 6px -1px rgba(59, 130, 246, 0.3);
}

@media (max-width: 640px) {
  .calendar-container {
    margin: 1rem;
    padding: 1rem;
    border-radius: 12px;
  }
  
  .day-cell {
    padding: 0.75rem;
    font-size: 0.9em;
  }
  
  button {
    padding: 0.5rem 1rem;
    font-size: 0.9em;
  }
}
  </style>