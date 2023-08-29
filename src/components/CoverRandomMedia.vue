<template>
  <div class="random-media">
    <div class="cover-image">
      <img src="../assets/img/barbie-pie.jpg" />
    </div>
    <h1 class="title-movie">Barbie the movie</h1>
    <div class="statistics">
      <span class="pr-2">300M ⭐</span>
      <span>3.8 👁️</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CoverRandomMedia',
  props: {
    msg: String
  },
  data(){
    this.getRandomMedia()
  },
  methods: {
    getRandomMedia() {

    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .random-media {
    color: white;
    position: relative;
    height: 100vh;
  }

  .title-movie {
    position: absolute;
    bottom: 40px;
    text-align: center;
    width: 100%;
  }

  .statistics {
    position: absolute;
    bottom: 30px;
    text-align: center;
    width: 100%;
  }

  .cover-image {
    border-radius: 50%;
    display: inline-block;
    position: relative;
  }

  .cover-image img {
    height: 100vh;
    display: block;
    border:1px solid rgba(0,10,10,0);
  }

  .cover-image:after {
   content: "";
   display: block;
   width: 100%;
   height: 100%;
   background: radial-gradient(circle at center, rgba(0,10,10,0) 0%,rgba(0,10,10,1) 69%,rgba(0,10,10,1) 100%);
   position: absolute;
   top: 0;
   left: 0;
  }

  .pr-2 {
    padding-right: 1rem;
  }
</style>
