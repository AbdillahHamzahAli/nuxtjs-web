<template>
  <div
    :class="[
      'item-task d-flex align-items-start border-bottom pt-3 pb-4',
      isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12',
      task.category === 'hard'
        ? 'bg-danger'
        : task.category === 'medium'
        ? 'bg-warning'
        : 'bg-success',
    ]"
  >
    <input
      id="task"
      v-model="localTask.isDone"
      type="checkbox"
      name="status"
      class="me-2 mt-2"
      :checked="task.isDone"
    />
    <div
      :class="[
        'd-flex flex-column',
        task.isDone ? 'text-decoration-line-through fst-italic' : '',
      ]"
    >
      <div class="title-task mb-1">
        {{ task.title }}
      </div>
      <div class="description-task small text-muted">
        {{ task.description }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      default: null,
    },
    isGrid: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
  // data() {
  //   return {
  //     localTask: { ...this.task },
  //   }
  // },
  computed: {
    localTask: {
      get() {
        return this.task
      },
      set(newValue) {
        this.$emit('update:task', newValue)
      },
    },
  },
}
</script>
