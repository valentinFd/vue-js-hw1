<template>
  <Button @click="changeFilter('all')" text="all"/>
  <Button @click="changeFilter('car')" text="cars"/>
  <Button @click="changeFilter('motorcycle')" text="motorcycles"/>
  <div v-for="item in getFilteredData(filter)" :key="item.brand">
    {{ item.brand }}
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Button from './components/Button.vue'

export default defineComponent({
  name: 'App',
  components: {
    Button
  },
  methods: {
    changeFilter (filter: string): void {
      this.$data.filter = filter
    },
    getFilteredData (filter: string): { type: string; brand: string }[] {
      if (filter === 'all') return this.items
      const result: { type: string; brand: string }[] = []
      this.items.forEach(function (item) {
        if (item.type === filter) result.push(item)
      })
      return result
    }
  },
  data () {
    return {
      filter: 'all',
      items: [
        {
          type: 'car',
          brand: 'Toyota'
        },
        {
          type: 'car',
          brand: 'Mazda'
        },
        {
          type: 'car',
          brand: 'Mitsubishi'
        },
        {
          type: 'motorcycle',
          brand: 'Suzuki'
        },
        {
          type: 'motorcycle',
          brand: 'Yamaha'
        },
        {
          type: 'motorcycle',
          brand: 'Honda'
        }
      ]
    }
  }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
