<template>
  <div class="Board col-4">
    <div class=" m-auto pt-5" @click='selectBoard()'>
      
<!-- Card -->
<div class="card card-image shadow">
  <!-- style="background-image: url(https://mdbootstrap.com/img/Photos/Horizontal/Work/4-col/img%20%2814%29.jpg);" -->

  <!-- Content -->
  <div class="text-black text-center align-items-center rgba-black-strong py-5 px-4">
    <div>
      <h5>{{boardData.title}}</h5>
      <h3 class="card-title pt-2"><strong>{{boardData.description}}</strong></h3>
      <p>{{boardData.creatorEmail}}</p>
    </div>
  </div>

</div>
<!-- Card -->


      <!-- <div class="card ">
       
        <div class="avatar mx-auto white">
          <img
            src="https://mdbootstrap.com/img/Photos/Avatars/img%20%2810%29.jpg"
            class="rounded-circle"
            alt="woman avatar"
          />
        </div>
        
        <div class="card-body">
          
          <h3>{{boardData.title}}</h3>
          <h4 class="card-title">{{boardData.description}}</h4>
          <hr />
         
          <p>
            {{boardData.creatorEmail}}
          </p>
        </div>
      </div> -->
     
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
    }
  },
  components: {}
};
</script>


<style scoped>
</style>