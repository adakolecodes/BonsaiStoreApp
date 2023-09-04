<template>
    <div id="carouselExampleCaptions" class="carousel slide carousel-fade" data-bs-ride="carousel">
      <div class="carousel-indicators">
        <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
        <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="1" aria-label="Slide 2"></button>
        <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="2" aria-label="Slide 3"></button>
      </div>
      <div class="carousel-inner">
        <div class="carousel-item active">
          <img src="../assets/images/bonsai1.jpeg" class="d-block w-100" alt="...">
          <div class="carousel-caption d-none d-md-block">
            <h1>WELCOME TO BONSAI</h1>
            <p>We supply Britain with the finest Bonsai material such as Trees, Bonsai Pots, Bonsai Tools, Bonsai Books and Bonsai Sundries.</p>
          </div>
        </div>
        <div class="carousel-item">
          <img src="../assets/images/bonsai2.jpeg" class="d-block w-100" alt="...">
          <div class="carousel-caption d-none d-md-block">
            <h1>INDOOR AND OUTDOOR</h1>
            <p>Bonsai growers often regard our outdoor plants as the 'real bonsai' Although, indoor bonsai have also become extremely popular in recent yearS.</p>
          </div>
        </div>
        <div class="carousel-item">
          <img src="../assets/images/bonsai3.jpeg" class="d-block w-100" alt="...">
          <div class="carousel-caption d-none d-md-block">
            <h1>BONSAI CARE</h1>
            <p>We stock a very comprehensive range of bonsai tools, soils and sundries. Our range of tools include the high quality Japanese tools, and the cheaper budget tools from China</p>
          </div>
        </div>
      </div>
      <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
</template>

<script>
    export default {
        name: 'CarouselComponent',
    }
</script>

<style scoped>

</style>