<template>
  <main>
    <div class="container py-5">
      <div class="row">
        <div class="col-8">
          <h4 class="mb-3">Room</h4>

          <draggable
            class="list-group room"
            v-model="list1"
            group="my-group"
            tag="transition-group"
            @start="drag = true"
            @end="drag = false"
            v-bind="dragOptions"
            :component-data="{
              tag: 'ul',
              type: 'transition-group',
              name: !drag ? 'flip-list' : null,
            }"
          >
            <template #item="{ element }">
              <li class="card shadow p-4">{{ element.name }}</li>
            </template>
          </draggable>
        </div>

        <div class="col">
          <div class="row">
            <h4 class="mb-3">Parks</h4>

            <draggable
              class="list-group park"
              v-model="list2"
              group="my-group"
              tag="transition-group"
              @start="drag = true"
              @end="drag = false"
              v-bind="dragOptions"
              :component-data="{
                tag: 'ul',
                type: 'transition-group',
                name: !drag ? 'flip-list' : null,
              }"
            >
              <template #item="{ element }">
                <li class="card shadow p-4">{{ element.name }}</li>
              </template>
            </draggable>
          </div>

          <div class="row mt-3">
            <draggable
              class="list-group park"
              v-model="list3"
              group="my-group"
              tag="transition-group"
              @start="drag = true"
              @end="drag = false"
              v-bind="dragOptions"
              :component-data="{
                tag: 'ul',
                type: 'transition-group',
                name: !drag ? 'flip-list' : null,
              }"
            >
              <template #item="{ element }">
                <li class="card shadow p-4">{{ element.name }}</li>
              </template>
            </draggable>
          </div>

          <div class="row mt-3">
            <draggable
              class="list-group park"
              v-model="list4"
              group="my-group"
              tag="transition-group"
              @start="drag = true"
              @end="drag = false"
              v-bind="dragOptions"
              :component-data="{
                tag: 'ul',
                type: 'transition-group',
                name: !drag ? 'flip-list' : null,
              }"
            >
              <template #item="{ element }">
                <li class="card shadow p-4">{{ element.name }}</li>
              </template>
            </draggable>
          </div>

          <div class="row mt-3">
            <draggable
              class="list-group park"
              v-model="list5"
              group="my-group"
              tag="transition-group"
              @start="drag = true"
              @end="drag = false"
              v-bind="dragOptions"
              :move="limitList"
              :component-data="{
                tag: 'ul',
                type: 'transition-group',
                name: !drag ? 'flip-list' : null,
              }"
            >
              <template #item="{ element }">
                <li class="card shadow p-4">{{ element.name }}</li>
              </template>
            </draggable>
          </div>
          <div class="row mt-3">
            <draggable
              class="list-group park"
              v-model="list6"
              group="my-group"
              tag="transition-group"
              @start="drag = true"
              @end="drag = false"
              v-bind="dragOptions"
              :component-data="{
                tag: 'ul',
                type: 'transition-group',
                name: !drag ? 'flip-list' : null,
              }"
            >
            <!-- :move="() => { if (list6.length >= 1) return false }" -->
              <template #item="{ element }">
                <li class="card shadow p-4">{{ element.name }}</li>
              </template>
            </draggable>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
<script>
import draggable from "vuedraggable";
export default {
  components: {
    draggable,
  },
  data() {
    return {
      list1: [
        { id: 1, name: "1" },
        { id: 2, name: "2" },
        { id: 3, name: "3" },
        { id: 4, name: "4" },
        { id: 5, name: "5" },
        { id: 6, name: "6" },
      ],
      list2: [],
      list3: [],
      list4: [],
      list5: [],
      list6: [],
    };
  },
  computed: {
    dragOptions() {
      return {
        animation: 200,
        group: "description",
        disabled: false,
        ghostClass: "ghost",
      };
    },
  },
};
</script>
<style scoped>
ul {
  list-style: none !important;
}

li {
  cursor: move !important;
  height: fit-content;
}

ul.room {
  display: grid;
  grid-template-columns: repeat(auto-fill, 200px);
  grid-auto-rows: max-content;
  gap: 1rem;
  height: 100%;
}

ul.park {
  display: grid;
  gap: 1rem;
  height: 106px;
  padding: 1rem;
  background-color: #e6e6e6;
}

.flip-list-move {
  transition: transform 0.5s;
}

.no-move {
  transition: transform 0s;
}

.ghost {
  opacity: 0.5;
  background: #e6e6e6;
}

.list-group {
  min-height: 20px;
}

</style>
