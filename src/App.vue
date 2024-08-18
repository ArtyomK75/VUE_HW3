<script>
import Products from './components/Products.vue'
import Task1 from './components/Task1.vue'
import Task2 from './components/Task2.vue'
import Task3 from './components/Task3.vue'
import Task4 from './components/Task4.vue'

export default {
  name: 'App',
  components: {
    Products,
    Task1,
    Task2,
    Task3,
    Task4,
  },
  data() {
    return {
      selectedComponent: null,
      theme: 'light'
    }
  },
  methods: {
    updateParentTheme(theme) {
      console.log(this.theme === 'light');
      this.theme = theme;
    }
  }
}
</script>

<template>

  <div class="flex flex-wrap gap-4" :class="theme">
    <label>
      <input type="radio" value="products" v-model="selectedComponent" />
      Products
    </label>
    <label>
      <input type="radio" value="task1" v-model="selectedComponent" />
      Task 1
    </label>
    <label>
      <input type="radio" value="task2" v-model="selectedComponent" />
      1. Події користувача та Модіфікатори подій
    </label>
    <label>
      <input type="radio" value="task3" v-model="selectedComponent" />
      2. Динамічні Стилі
    </label>
    <label>
      <input type="radio" value="task4" v-model="selectedComponent" />
      3. Директива v-for
    </label>
    <Products v-show="selectedComponent === 'products'" />
    <Task1 v-if="selectedComponent === 'task1'" />
    <Task2 v-show="selectedComponent === 'task2'" />
    <Task3 v-show="selectedComponent === 'task3'" :theme="theme" @theme-chenged="updateParentTheme"/>
    <Task4 v-show="selectedComponent === 'task4'" />
  </div>
</template>

<style>
  .light {
    background-color: white;
    color: black;
  }
  .dark {
    background-color: black;
    color: white;
  }
</style>