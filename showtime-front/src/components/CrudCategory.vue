<template>
  <h2>Crud Categories</h2>
  <button
    type="button"
    class="btn btn-primary m-2 fload-end"
    data-bs-toggle="modal"
    data-bs-target="#categoryModal"
    @click="addCategoryClick()"
  >
    Add Category
  </button>
  <div class="container">
    <table class="table table-striped">
      <thead>
        <tr>
          <th>Id</th>
          <th>Name</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(category, index) in categories" :key="index">
          <td>{{ category.id }}</td>
          <td>{{ category.name }}</td>
          <td>
            <button
              type="button"
              class="btn btn-light mr-1"
              data-bs-toggle="modal"
              data-bs-target="#categoryModal"
              @click="editCategoryClick(category)"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="16"
                height="16"
                fill="currentColor"
                class="bi bi-pencil-square"
                viewBox="0 0 16 16"
              >
                <path
                  d="M15.502 1.94a.5.5 0 0 1 0 .706L14.459 3.69l-2-2L13.502.646a.5.5 0 0 1 .707 0l1.293 1.293zm-1.75 2.456-2-2L4.939 9.21a.5.5 0 0 0-.121.196l-.805 2.414a.25.25 0 0 0 .316.316l2.414-.805a.5.5 0 0 0 .196-.12l6.813-6.814z"
                />
                <path
                  fill-rule="evenodd"
                  d="M1 13.5A1.5 1.5 0 0 0 2.5 15h11a1.5 1.5 0 0 0 1.5-1.5v-6a.5.5 0 0 0-1 0v6a.5.5 0 0 1-.5.5h-11a.5.5 0 0 1-.5-.5v-11a.5.5 0 0 1 .5-.5H9a.5.5 0 0 0 0-1H2.5A1.5 1.5 0 0 0 1 2.5v11z"
                />
              </svg>
            </button>
            <button
              type="button"
              class="btn btn-light mr-1"
              v-on:click="deleteCategory(category.id)"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="16"
                height="16"
                fill="currentColor"
                class="bi bi-trash3-fill"
                viewBox="0 0 16 16"
              >
                <path
                  d="M11 1.5v1h3.5a.5.5 0 0 1 0 1h-.538l-.853 10.66A2 2 0 0 1 11.115 16h-6.23a2 2 0 0 1-1.994-1.84L2.038 3.5H1.5a.5.5 0 0 1 0-1H5v-1A1.5 1.5 0 0 1 6.5 0h3A1.5 1.5 0 0 1 11 1.5Zm-5 0v1h4v-1a.5.5 0 0 0-.5-.5h-3a.5.5 0 0 0-.5.5ZM4.5 5.029l.5 8.5a.5.5 0 1 0 .998-.06l-.5-8.5a.5.5 0 1 0-.998.06Zm6.53-.528a.5.5 0 0 0-.528.47l-.5 8.5a.5.5 0 0 0 .998.058l.5-8.5a.5.5 0 0 0-.47-.528ZM8 4.5a.5.5 0 0 0-.5.5v8.5a.5.5 0 0 0 1 0V5a.5.5 0 0 0-.5-.5Z"
                />
              </svg>
            </button>
          </td>
        </tr>
      </tbody>
    </table>
    <div
      class="modal fade"
      id="categoryModal"
      tabindex="-1"
      aria-labelleBy="categoryModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog modal-lg modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="categoryModalLabel">
              {{ modalTitle }}
            </h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="modal-body">
            <div class="input-group mb-3">
              <span class="input-group-text">Name</span>
              <input type="text" class="form-control" v-model="name" required />
            </div>
            <button
              type="button"
              @click="createCategory()"
              v-if="id == 0"
              class="btn btn_primary"
              data-bs-dismiss="modal"
              aria-label="Close"
            >
              Create Category
            </button>
            <button
              type="button"
              v-on:click="updateCategory(id)"
              v-if="id != 0"
              class="btn btn_primary"
              data-bs-dismiss="modal"
              aria-label="Close"
            >
              Update Category
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { useStore } from "vuex";
export default {
  name: "CrudCategory",
  components: {},
  props: {
    category: Object,
  },
  data() {
    return { store: useStore(), modalTitle: "", id: 0, name: "" };
  },
  computed: {
    categories: function () {
      return this.store.getters.getCategories;
    },
  },
  mounted() {
    this.store.dispatch("getAllCategories");
  },
  methods: {
    addCategoryClick() {
      this.modalTitle = "ADD CATEGORY";
      this.id = 0;
      this.name = "";
    },
    editCategoryClick(category) {
      this.modalTitle = "EDIT CATEGORY";
      this.id = category.id;
      this.name = category.name;
    },
    createCategory: async function () {
      this.store.dispatch("createCategory", {
        name: this.name,
      });
    },
    deleteCategory: async function (id) {
      this.store.dispatch("deleteCategory", { id });
    },
    updateCategory: async function (id) {
      this.store.dispatch("updateCategory", {
        id: id,
        name: this.name,
      });
    },
  },
};
</script>
<style>
.container {
  width: 100%;
  height: 100vh;
  margin: 0 auto;
  overflow-x: hidden;
}
</style>
