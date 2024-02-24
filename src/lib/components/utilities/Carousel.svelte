<script>
    let carouselImage;
    let index = 0;
  
    function updateAccessory() {
      carouselImage.style.transform = `translateX(${-100 * index}%)`;
      console.log(index, "index")
    }
  
    function previous() {
      const previousButton = document.querySelector('.previous-button ');
      const nextButton = document.querySelector('.nextButton');
  
      nextButton.classList.remove('inactive');
      if (index > -1) {
        index -= 1;
      }
  
      if (index < 0) {
       index = 4;
      }
      updateAccessory();
    }
  
    function next() {
      const previousButton = document.querySelector('.previous-button');
      const nextButton = document.querySelector('.nextButton');
  
      previousButton.classList.remove('inactive');
  
      if (index < 5) {
        index += 1;
      }
  
      if (index > 4) {
       index = 0;
      }
  
      updateAccessory();
    }
  </script>
  
  <div class="carousel">
    <div class="carouselImage" bind:this={carouselImage}>
        <div class="contenaireImg">
            <img src="dessin/Nebula.jpg" alt="dessin">
        </div>
        <div class="contenaireImg">
            <img src="/dessin/Max.jpg" alt="dessin">
        </div>
        <div class="contenaireImg">
            <img src="/dessin/femme_blonde.jpg" alt="dessin">
        </div>
        <div class="contenaireImg">
            <img src="/dessin/femme_profil.jpg" alt="dessin">
        </div>
        <div class="contenaireImg">
            <img src="/dessin/Wanda.jpg" alt="dessin">
        </div>
     
    </div>
  
    <img class="previous-button button" src="/back.svg" alt="Preview" on:click={previous}>
    <img class="nextButton button" src="/next.svg" alt="Preview" on:click={next}>
  </div>
  
  <style>

    .carousel{
        overflow: hidden;
        width: 600px;
    }
    .carouselImage {

        transition: 0.25s ease-in;
      width: 600px;
      height: 703px;
    }
  
    img {
        width: 100%; /* Pour remplir entièrement le conteneur */
        height: 100%; /* Pour remplir entièrement le conteneur */
        object-fit: cover; /* Pour s'assurer que l'image remplit entièrement le conteneur sans déformation */
    }
    .contenaireImg{
        width: 600px;
        height: 600px;
        overflow: hidden;
        position: absolute;
        border-radius: 20px;
        transition: 1s ease-in;
    }

    .button{
        width: 50px;
        height: 50px;
    }
  
    .carouselImage > *:nth-child(1) {
    transform: translateX(0);
  }
  .carouselImage > *:nth-child(2) {
    transform: translateX( 100%);
  }
  .carouselImage > *:nth-child(3) {
    transform: translateX( 200%);
  }
  .carouselImage > *:nth-child(4) {
    transform: translateX( 300%);
  }

  .carouselImage > *:nth-child(5) {
    transform: translateX( 400%);
  }

  .carouselImage > *:nth-child(6) {
    transform: translateX( 500%);
  }
  </style>
  