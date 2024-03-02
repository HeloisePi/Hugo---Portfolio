<script>
    export let taille;
    let carouselImage;
    let index = 0;
  
    function updateAccessory() {
        carouselImage.style.transform = `translateX(${-100 * index}%)`;
        console.log(index, "index");
    }
  
    function previous() {
        const previousButton = document.querySelector('.previous-button');
        const nextButton = document.querySelector('.nextButton');
  
        nextButton.classList.remove('inactive');
        if (index > 0) {
            index -= 1;
        } else {
            index = 4;
        }
  
        updateAccessory();
    }
  
    function next() {
        const previousButton = document.querySelector('.previous-button');
        const nextButton = document.querySelector('.nextButton');
  
        previousButton.classList.remove('inactive');
  
        if (index < taille-1) {
            index += 1;
        } else {
            index = 0;
        }
  
        updateAccessory();
    }
</script>
  
<div class="carousel">
    <div class="carouselImage" bind:this={carouselImage}>
            <slot></slot>
    </div>
    <div class="contenaireButton">
    <img class="previous-button button" src="/back.svg" alt="Preview" on:click={previous}>
    <img class="nextButton button" src="/next.svg" alt="Preview" on:click={next}>

    </div>
</div>

  
<style>

    .contenaireButton {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 480px;
        height: 300px;
        position: relative;
    }
    .carousel {
        overflow: hidden;
        width: 480px;
        height: 300px;
        position: relative;
    }

    .carouselImage {
        display: flex;
        transition: 0.25s ease-in;
        width: 480px;
        height: 300px;
        position: absolute;

        top: 0;
        left: 0;
    }


    .button {
        width: 50px;
        height: 50px;
        z-index: 100000000;
    }

    @media screen and (max-width: 635px) {
        .contenaireButton {
            width: 300px;

        }
        .carousel {
            width: 300px;
        }
        .carouselImage {
            width: 300px;
        }

    }
</style>