<template>
  <div class="py-4">
    <div class="container">
      <div
        class="title border-bottom d-flex align-items-center justify-content-between py-2"
      >
        <h5>Task</h5>
        <h5 class="ms-2">
          Category : {{ categoryQuery === '' ? 'All' : categoryQuery }}
        </h5>

        <div class="d-flex align-items-center ms-auto">
          <input
            v-model="searchQuery"
            type="text"
            class="form-control"
            placeholder="Search"
          />
          <div class="ms-2 dropdown">
            <button
              class="btn btn-secondary dropdown-toggle"
              type="button"
              data-bs-toggle="dropdown"
              aria-expanded="false"
            >
              Category
            </button>
            <ul class="dropdown-menu">
              <li>
                <button
                  class="dropdown-item py-1 px-3"
                  @click="categoryQuery = 'Hard'"
                >
                  Hard
                </button>
              </li>
              <li>
                <button
                  class="dropdown-item py-1 px-3"
                  @click="categoryQuery = 'Medium'"
                >
                  Medium
                </button>
              </li>
              <li>
                <button
                  class="dropdown-item py-1 px-3"
                  @click="categoryQuery = 'Eazy'"
                >
                  Eazy
                </button>
              </li>
              <li><hr class="dropdown-divider" /></li>
              <li>
                <button
                  class="dropdown-item py-1 px-3"
                  @click="categoryQuery = ''"
                >
                  All
                </button>
              </li>
            </ul>
          </div>

          <div class="d-flex align-items-center justify-content-end w-100">
            <span class="me-2">View As</span>
            <button
              class="btn btn-outline-secondary py-1 px-3"
              @click="isGrid = !isGrid"
            >
              {{ isGrid ? 'Grid' : 'List' }}
            </button>
          </div>
        </div>
      </div>
      <!-- Tasks -->
      <div v-if="loading" class="text-center m-5">
        <div class="spinner-border" role="status">
          <span class="visually-hidden">Loading...</span>
        </div>
      </div>

      <div v-else class="list-task row">
        <CardItem
          v-for="(item, i) in resultQuery"
          :key="i"
          :task="item"
          :isGrid="isGrid"
        />
      </div>
      <!-- Tasks -->
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
import CardItem from '@/components/Card/CardItem.vue'
export default {
  components: {
    CardItem,
  },
  layout(context) {
    return 'default'
  },

  data() {
    return {
      tasks: [],
      isCreating: false,
      isGrid: false,
      searchQuery: '',
      categoryQuery: '',
      loading: '',
    }
  },
  computed: {
    resultQuery() {
      return this.tasks.filter((item) => {
        const titleContainsKeywords = this.searchQuery
          .toLowerCase()
          .split(' ')
          .every((v) => item.title.toLowerCase().includes(v))

        const categoryMatches =
          item.category.toLowerCase() === this.categoryQuery.toLowerCase() ||
          this.categoryQuery === ''

        return this.searchQuery || this.categoryQuery
          ? titleContainsKeywords && categoryMatches
          : true
      })
    },
  },
  created() {
    this.loading = true
  },
  mounted() {
    setTimeout(() => {
      this.tasks = [
        {
          title: 'Task 1',
          description: 'ini deskripsi 1',
          isDone: false,
          category: 'Hard',
        },
        {
          title: 'Task 2',
          description: 'ini deskripsi 2',
          isDone: false,
          category: 'Medium',
        },
        {
          title: 'Task 3',
          description: 'ini deskripsi 3',
          isDone: false,
          category: 'Eazy',
        },
        {
          title: 'Task 4',
          description: 'ini deskripsi 4',
          isDone: false,
          category: 'Medium',
        },
        {
          title: 'Task 5',
          description: 'ini deskripsi 5',
          isDone: false,
          category: 'Eazy',
        },
        {
          title: 'Task 6',
          description: 'ini deskripsi 6',
          isDone: false,
          category: 'Hard',
        },
      ]
      this.loading = false
    }, 5000)
  },
}
</script>
<style></style>
