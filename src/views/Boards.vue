<template>
  <div class="boards container-fluid">
    <!-- <div class="row mt-5">
      WELCOME TO THE BOARDS!!!
      <form @submit.prevent="addBoard">
        <input type="text" placeholder="title" v-model="newBoard.title" required />
        <input type="text" placeholder="description" v-model="newBoard.description" />
        <button type="submit">Create Board</button>
      </form>
    </div> -->
    <div class="row">
      <CreateBoard v-if="$auth.isAuthenticated" />
      <small class="text-danger" v-else>You must log in to create a board!</small>
    </div>
    <div class="row m-auto">
       
      <board v-for="board in boards" :boardData="board" :key="board.id" />
      <!-- NOTE old way of loading boards 
      <router-link :to="{name: 'board', params: {boardId: board.id}}">{{board.title}}</router-link>-->
    </div>
  </div>
</template>

<script>
import CreateBoard from "../components/CreateBoard.vue";
import Board from "../components/Board.vue";
export default {
  name: "boards",
  mounted() {
    this.$store.dispatch("getBoards");
  },
  data() {
    return {
      // newBoard: {
      //   title: "",
      //   description: ""
      // }
    };
  },
  computed: {
    boards() {
      return this.$store.state.boards;
    }
  },
  methods: {
    
  },
  components: {
    Board,
    CreateBoard
  }
};
</script>