<template>
  <div class="py-4">
    <div class="container">
      <div class="title border-bottom">
        <h5>Task</h5>
      </div>
      <div class="list-task">
        <div class="item-task d-flex align-items-start border-bottom pt-3 pb-4">
          <input
            id="task"
            type="checkbox"
            name="status"
            class="me-2 mt-2"
            :checked="tasks[0].isDone"
          />
          <div class="d-flex flex-column">
            <div class="title-task mb-1">
              {{ tasks[0].title }}
            </div>
            <div class="description-task small text-muted">
              {{ tasks[0].description }}
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
          description: 'ini deskripsi',
          isDone: false,
        },
      ],
      isCreating: false,
    }
  },
}
</script>
<style></style>
