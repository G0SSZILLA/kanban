<template>
  <div class="Board col-4">
    <div class="m-auto pt-5" @click="selectBoard()">
      <!-- Card -->
      <div class="card card-image shadow">
      
        <!-- style="background-image: url(https://mdbootstrap.com/img/Photos/Horizontal/Work/4-col/img%20%2814%29.jpg);" -->
        <div class="text-black text-center align-items-center rgba-black-strong py-5 px-4">
          <div>
            <h5>{{boardData.title}}</h5>
            <h3 class="card-title pt-2">
              <strong>{{boardData.description}}</strong>
            </h3>
            <p>{{boardData.creatorEmail}}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "Board",
  props: ["boardData"],
  data() {
    return {};
  },
  computed: {},
  methods: {
    selectBoard() {
      this.$store.commit("setActiveBoard", {});
      this.$router.push({
        name: "board",
        params: { boardId: this.boardData._id }
      });
    },
    
  },
  components: {}
};
</script>


<style scoped>
</style>