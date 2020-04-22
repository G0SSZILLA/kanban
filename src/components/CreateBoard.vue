<template>
  <div class="createBoard col-4 m-auto">
    <!-- Card -->
    <div class="card shadow bg-white">
      <!-- Card content -->
      <div class="card-body">
        <!-- Title -->
        <h4 class="card-title text-center">
          <a>Create a board!</a>
        </h4>
        <!-- Text -->
        <p class="card-text shadow">
          <input
            type="text"
            class="form-control"
            placeholder="Board Title..."
            v-model="newBoard.title"
          />
          <input
            type="text"
            class="form-control"
            placeholder="Board Description..."
            v-model="newBoard.description"
          />
        </p>
        <!-- Button -->
        <button type="button" class="btn btn-primary" @click="addBoard()">Add</button>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "createBoard",
  data() {
    return {
      newBoard: {}
    };
  },
  computed: {},
  methods: {
    addBoard() {
      this.$store.dispatch("addBoard", this.newBoard);
      this.newBoard = { title: "", description: "" };
    }
  },
  components: {}
};
</script>


<style scoped>
</style>