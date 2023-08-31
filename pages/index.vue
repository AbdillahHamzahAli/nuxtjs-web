<template>
  <div class="py-4">
    <div class="container">
      <div
        class="title border-bottom d-flex align-items-center justify-content-between py-2"
      >
        <h5>Task</h5>
        <div class="d-flex align-items">
          <span class="me-2">View as</span>
          <button
            class="btn btn-outline-secondary py-1 px-3"
            @click="isGrid = !isGrid"
          >
            {{ isGrid ? 'Grid' : 'List' }}
          </button>
        </div>
      </div>
      <div class="list-task row">
        <div
          :class="[
            'item-task d-flex align-items-start border-bottom pt-3 pb-4',
            isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12',
          ]"
        >
          <input
            id="task"
            v-model="tasks[0].isDone"
            type="checkbox"
            name="status"
            class="me-2 mt-2"
            :checked="tasks[0].isDone"
          />
          <div
            :class="[
              'd-flex flex-column',
              tasks[0].isDone ? 'text-decoration-line-through fst-italic' : '',
            ]"
          >
            <div class="title-task mb-1">
              {{ tasks[0].title }}
            </div>
            <div class="description-task small text-muted">
              {{ tasks[0].description }}
            </div>
          </div>
        </div>
        <div
          :class="[
            'item-task d-flex align-items-start border-bottom pt-3 pb-4',
            isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12',
          ]"
        >
          <input
            id="task"
            v-model="tasks[1].isDone"
            type="checkbox"
            name="status"
            class="me-2 mt-2"
            :checked="tasks[1].isDone"
          />
          <div
            :class="[
              'd-flex flex-column',
              tasks[1].isDone ? 'text-decoration-line-through fst-italic' : '',
            ]"
          >
            <div class="title-task mb-1">
              {{ tasks[1].title }}
            </div>
            <div class="description-task small text-muted">
              {{ tasks[1].description }}
            </div>
          </div>
        </div>
        <div
          :class="[
            'item-task d-flex align-items-start border-bottom pt-3 pb-4',
            isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12',
          ]"
        >
          <input
            id="task"
            v-model="tasks[2].isDone"
            type="checkbox"
            name="status"
            class="me-2 mt-2"
            :checked="tasks[2].isDone"
          />
          <div
            :class="[
              'd-flex flex-column',
              tasks[2].isDone ? 'text-decoration-line-through fst-italic' : '',
            ]"
          >
            <div class="title-task mb-1">
              {{ tasks[2].title }}
            </div>
            <div class="description-task small text-muted">
              {{ tasks[2].description }}
            </div>
          </div>
        </div>
      </div>
      <div class="action py-2">
        <a
          v-if="!isCreating"
          href="#"
          class="add-button"
          @click="isCreating = !isCreating"
          >Add Task</a
        >
        <div v-else class="add-card">
          <div class="card mb-2">
            <div class="card-body d-flex flex-column p-0">
              <input
                class="form-control border-0 mb-2"
                placeholder="Title"
                type="text"
              />
              <textarea
                class="form-control border-0 small"
                placeholder="Description"
                rows="3"
              ></textarea>
            </div>
          </div>
          <div class="button-wrapper d-flex">
            <button class="btn btn-primary me-2">Save</button>
            <button
              class="btn btn-outline-secondary"
              @click="isCreating = !isCreating"
            >
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      tasks: [
        {
          title: 'Task 1',
          description: 'ini deskripsi 1',
          isDone: false,
        },
        {
          title: 'Task 2',
          description: 'ini deskripsi 2',
          isDone: false,
        },
        {
          title: 'Task 3',
          description: 'ini deskripsi 3',
          isDone: false,
        },
      ],
      isCreating: false,
      isGrid: false,
    }
  },
}
</script>
<style></style>
