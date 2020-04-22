<template>
  <div class="board">
    <button
              v-if="$auth.isAuthenticated"
              class="btn btn-danger shadow"
              @click="deleteBoard()"
            >Delete</button>
              <span>
            <button
              v-if="$auth.isAuthenticated"
              class="btn btn-warning shadow"
              @click="editing = !editing"
            >Edit Board</button>
            <form v-if="editing" @submit.prevent="editBoard">
              <input type="text" v-model="board.title" />
              <button
                type="submit"
                v-if="$auth.isAuthenticated"
                class="btn btn-primary shadow"
              >Confirm</button>
            </form>
            </span>
    <h1 v-if="board.title">{{board.title}}</h1>
    
  </div>
</template>

<script>
export default {
  name: "board",
  // props: ['blogId'],
  data(){
    return {
      editing: false
    };
  },
    mounted(){
this.$store.dispatch('getBoard', this.$route.params.boardId)
    },
  computed: {
    board() {
      return this.$store.state.activeBoard;
    }
  },
  methods: {
    deleteBoard(){
      this.$store.dispatch("deleteBoard", this.$route.params.boardId)
      this.$router.push({name: 'boards'})
    },
    editBoard(){
      this.$store.dispatch("editBoard", this.board)
      this.editing = false
    }
  },
};
</script>
