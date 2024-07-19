<template>
  <div class="accordion">
    <div
      v-for="(item, index) in items"
      :key="index"
      class="accordion-item"
      :ref="`accordionItem${index}`"
    >
      <div class="accordion-header" @click="toggle(index, $refs[`accordionItem${index}`])">
        <h2>{{ item.title }}</h2>
      </div>
      <div v-if="activeIndex === index" class="accordion-body">
        <p>{{ item.content }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Accordion',
  props: {
    items: {
      type: Array,
      required: true,
      default: () => []
    }
  },
  setup () {
    const activeIndex = ref(null)

    const toggle = (index, elementRef) => {
      if (activeIndex.value === index) {
        activeIndex.value = null
      } else {
        activeIndex.value = index
        if (elementRef && elementRef[0]) {
          elementRef[0].scrollIntoView({ behavior: 'smooth', block: 'start' })
        }
      }
    }

    return { activeIndex, toggle }
  }
}
</script>

<style scoped>
.accordion {
  border: 1px solid #ddd;
}

.accordion-item {
  border-bottom: 1px solid #ddd;
}

.accordion-header {
  background: #f8f9fa;
  padding: 1rem;
  cursor: pointer;
}

.accordion-body {
  padding: 1rem;
}
</style>
