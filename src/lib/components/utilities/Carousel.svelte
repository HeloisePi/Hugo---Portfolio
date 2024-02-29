<script>
    let carouselImage;
    let index = 0;
    const totalItems = 5; // Nombre total d'éléments dans le carousel

    function updateAccessory() {
        const leftPosition = -100 * index;
        carouselImage.style.left = `${leftPosition}%`;

        const centerImgContainers = document.querySelectorAll('.contenaireImg');
        centerImgContainers.forEach(container => {
            container.style.transform = 'scale(100%)';
            container.style.zIndex = '1';
        });

        const centerImgContainer = carouselImage.children[index];
        centerImgContainer.style.transform = 'scale(135%)';
        centerImgContainer.style.zIndex = '90';
    }
  
    function previous() {
        if (index > -1) {
            index -= 1;
        }
  
        if (index < 0) {
            index = 4;
        }
        updateAccessory();
    }
  
    function next() {
        if (index < 5) {
            index += 1;
        }
  
        if (index > 4) {
            index = 0;
        }
  
        updateAccessory();
    }

    function goToIndex(i) {
        index = i;
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
    <div class="contenaireButton">
        <img class="previous-button button" src="/back.svg" alt="Preview" on:click={previous}>
        <img class="nextButton button" src="/next.svg" alt="Preview" on:click={next}>
    </div>
    <div class="points">
        {#each Array(totalItems) as _, i}
            <div class="point {i === index ? 'active' : ''}" on:click={() => goToIndex(i)}></div>
        {/each}
    </div>
    
</div>
<style lang="scss">
    @import '../../styles/global.scss';
    .contenaireButton .previous-button{
        transform: translate(-20vw, 0vw);
    }

    .contenaireButton .nextButton{
        transform: translate(20vw, 0vw);
    }

    .carousel .center {
        transform: scale(110%) !important;
        z-index: 30;
        background-color: lightblue; /* Ajout d'une couleur de fond pour s'assurer qu'il est visible */
    }

    .carousel {
        width: fit-content;
        position: relative;
        width: 600px;
        height: 1000px;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .carouselImage {
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
        transition: 0.25s ease-in;
        width: 600px;
        height: 1000px;
        position: absolute;
        left: 0%;
        top: 50%;
        transform: translate(0%, -50%);
        transition: 0.25s ease-in-out;
    }

    @media screen and (max-width: 2000px) {
        .carousel {
            width: 500px;
            height: 800px;
        }
        .carouselImage {
            width: 500px;
            .contenaireImg {
                width: 500px;
                height: 500px;
            }
        }
       .carousel .points{
            bottom: 14%;
        }
    }

    @media screen and (max-width: 1700px) {
        .carousel {
            width: 400px;
            height: 900px;
        }
        .carouselImage {
            width: 400px;
            .contenaireImg {
                width: 400px;
                height: 400px;
            }
        }
       .points{
            bottom: 17%;
        }
    }

    @media screen and (max-width: 1400px) {
        .carousel {
            width: 300px;
            height: 800px;
        }
        .carouselImage {
            width: 300px;
            .contenaireImg {
                width: 300px;
                height: 300px;
            }
        }
    }

    @media screen and (max-width: 1100px) {
        .carousel {
            width: 200px;
            height: 800px;
        }
        .carouselImage {
            width: 200px;
            .contenaireImg {
                width: 200px;
                height: 200px;
            }
        }
        .carousel .points{
            bottom: 27%;
        }
    }

    @media screen and (max-width: 650px) {
        .carousel {
            width: 300px;
            height: 700px;
        }
        .carouselImage {
            width: 300px;
            .contenaireImg {
                width: 300px;
                height: 300px;
            }
        }

        .carousel .points{
            bottom: 13%;
        }
    }

    @media screen and (max-width: 475px) {
        .carousel {
            width: 200px;
            height: 600px;
        }
        .carouselImage {
            width: 200px;
            .contenaireImg {
                width: 200px;
                height: 200px;
            }
        }
    }

    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .contenaireImg {
        width: 600px;
        height: 600px;
        overflow: hidden;
        position: absolute;
        border-radius: 20px;
        transition: 0.25s ease-in;
    }

    .button {
        width: 50px;
        height: 50px;
        z-index: 1000000;
        transform: translate(10px, 10px);
    }

    .contenaireButton {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 80vw;
    }

    .carouselImage > *:nth-child(1) {
        left : 0;
    }

    .carouselImage > *:nth-child(2) {
        left :  100%;
    }

    .carouselImage > *:nth-child(3) {
        left :  200%;
    }

    .carouselImage > *:nth-child(4) {
        left :  300%;
    }

    .carouselImage > *:nth-child(5) {
        left :  400%;
    }

    .carouselImage > *:nth-child(6) {
        left :  500%;
    }

    /* Styles pour les points */
    .points {
        display: flex;
        justify-content: center;
        margin-top: 10px;
        position: absolute;
        bottom: 2%;
    }

    .point {
        width: 10px;
        height: 10px;
        background-color: white;
        border-radius: 50%;
        margin: 0 5px;
        transition: all 0.3s ease;
    }

    .point.active {
        background-color: $lightViolet;
        transform: scale(1.3);
    }

    .point:hover{
        transform: scale(1.5);
        
    }


</style>
