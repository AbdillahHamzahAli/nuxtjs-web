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
                  @click="categoryQuery = 'hard'"
                >
                  Hard
                </button>
              </li>
              <li>
                <button
                  class="dropdown-item py-1 px-3"
                  @click="categoryQuery = 'medium'"
                >
                  Medium
                </button>
              </li>
              <li>
                <button
                  class="dropdown-item py-1 px-3"
                  @click="categoryQuery = 'eazy'"
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

      <div class="action py-2">
        <a
          v-if="!isCreating"
          href="#"
          class="add-button"
          @click="isCreating = !isCreating"
          >Add Task</a
        >
        <div v-else class="add-card">
          <form v-on:submit.prevent="handleSubmit">
            <div class="mb-2">
              <div class="d-flex flex-column p-0">
                <div class="mb-3">
                  <label class="form-label">Title</label>
                  <input
                    v-model="form.title"
                    class="form-control mb-2"
                    placeholder="Title"
                    type="text"
                  />
                </div>
                <div class="mb-3">
                  <label class="form-label">Deskripsi</label>
                  <textarea
                    v-model="form.description"
                    class="form-control small"
                    placeholder="description"
                    rows="3"
                  ></textarea>
                </div>
                <div class="mb-3">
                  <label class="form-label">Category</label>
                  <select v-model="form.category" class="form-select">
                    <option disabled value="">Nothing selected</option>
                    <option
                      v-for="(option, i) in options.categories"
                      :key="i"
                      :value="option.value"
                    >
                      {{ option.text }}
                    </option>
                  </select>
                </div>
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
          </form>
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
      <!-- End Tasks -->
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
      form: {
        title: '',
        description: '',
        isDone: false,
        category: '',
      },
      options: {
        categories: [
          { value: 'hard', text: 'HARD' },
          { value: 'medium', text: 'MEDIUM' },
          { value: 'eazy', text: 'EAZY' },
        ],
      },
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
          category: 'hard',
        },
        {
          title: 'Task 2',
          description: 'ini deskripsi 2',
          isDone: false,
          category: 'medium',
        },
        {
          title: 'Task 3',
          description: 'ini deskripsi 3',
          isDone: false,
          category: 'eazy',
        },
      ]
      this.loading = false
    }, 2000)
  },
  methods: {
    handleSubmit() {
      const item = {
        form: { ...this.form },
      }
      this.tasks.unshift(item.form)
    },
  },
}
</script>
<style></style>
