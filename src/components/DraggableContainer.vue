<template>
  <draggable
  v-model="list"
  tag="transition-group"
  item-key="order">
    <template #item="{ element }">
      <div>{{ element.name }}</div>
    </template>
  </draggable>
</template>

<script>
import draggable from "vuedraggable";

const message = [
  "vue.draggable",
  "draggable",
  "component",
  "for",
  "vue.js 2.0",
  "based",
  "on",
  "Sortablejs"
];

export default {
  components: {
    draggable,
  },
  data() {
    return {
    list: message.map((name, index) => {
        return { name, order: index + 1 };
    }),
    drag: false,
    };
  },
};
</script>
