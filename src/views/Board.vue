<template>
  <div class="board">
    <button
              v-if="$auth.isAuthenticated"
              class="btn btn-danger shadow"
              @click="deleteBoard()"
            >Delete</button>
    <h1 v-if="board.title">{{board.title}}</h1>
    
  </div>
</template>

<script>
export default {
  name: "board",
  // props: ['blogId'],
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
  },
};
</script>
