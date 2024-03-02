<script>
	import Carousel from "./utilities/Carousel.svelte";
	import MiniCarousel from "./utilities/MiniCarousel.svelte";


</script>

<h2>Dessin</h2>
<section>
	<div class="contenaireCarousel">
		<Carousel></Carousel>
	</div>
	<div class="miniCarousel">
		<MiniCarousel
		taille="5">
            <img class="carouselImage one" src="dessin/Nebula.jpg" alt="dessin">
            <img class="carouselImage two"src="/dessin/Max.jpg" alt="dessin">
            <img class="carouselImage thee"src="/dessin/femme_blonde.jpg" alt="dessin">
            <img class="carouselImage four"src="/dessin/femme_profil.jpg" alt="dessin">
            <img class="carouselImage five"src="/dessin/Wanda.jpg" alt="dessin">
		</MiniCarousel>
	</div>
	<a href="/dessin"><p class="seeemore">Tout découvrir</p></a>
</section>

<style lang="scss">


	a{
		z-index: 0;
	}
	.seeemore{
		text-decoration: underline;
		z-index: 0;
	}
	h2{
		margin: 0;
		margin-top: 148px;
	}
	section{
		display: flex;
		justify-content: center;
		align-items: center;
		width: 100%;
		flex-direction: column;
		z-index: 0;
		
	}
	.contenaireCarousel{
		width: 1800px;
		overflow: hidden;
		display: flex;
		justify-content: center;
		align-items: center;
		z-index: 0;
	}

	@media screen and (max-width: 2000px) {
        .contenaireCarousel{
			width: 1500px;
		}

        
    }

    @media screen and (max-width: 1700px) {
        .contenaireCarousel{
			width: 1200px;
		}
		// section a{
		// 	left: 23vw;
		// 	position: absolute;
		// 	bottom: 0;
		// }
    }

    @media screen and (max-width: 1400px) {
        .contenaireCarousel{
			width: 900px;
		}
		// section a{
		// 	left: 23vw;
		// 	position: absolute;
		// 	bottom: 0;
		// }

    }

    @media screen and (max-width: 1100px) {
        .contenaireCarousel{
			width: 600px;
		}
		// section a{
		// 	left: 27vw;
		// 	position: absolute;
		// 	bottom: 0;
		// }
    }


    @media screen and (max-width: 650px) {
        .contenaireCarousel{
			display: none;
		}

		section .miniCarousel{
			display: block;
		}
		
    }


	.miniCarousel{
		display: none;
	}

	.carouselImage{
        position: absolute;
        left: 0;
        top: 0;
        width: 480px;
        height: 100%;
        object-fit: contain;
		border-radius: 20px;
    }

    .one{
        left : 0;
    }

    .two{
        left : 480px;
    }

    .thee{
        left : calc(480px*2);
    }
    .four{
        left : calc(480px*3);
    }

    .five{
        left : calc(480px*4);
    }

    .six{
        left: calc(480px*5);
    }

    .seven{
        left: calc(480px*6);
    }

    .height{
        left: calc(480px*7);
    }

	@media screen and (max-width: 635px) {
        .carouselImage{
            width: 300px;
        }
        .two{
        left : 300px;
    }

    .thee{
        left : calc(300px*2);
    }
    .four{
        left : calc(300px*3);
    }

    .five{
        left : calc(300px*4);
    }

    .six{
        left: calc(300px*5);
    }
    .seven{
        left: calc(300px*6);
    }

    .height{
        left: calc(300px*7);
    }
    }

    @media screen and (max-width: 445px) {
        .carouselImage{
            width: 200px;
        }
        .two{
        left : 200px;
    }

    .thee{
        left : calc(200px*2);
    }
    .four{
        left : calc(200px*3);
    }

    .five{
        left : calc(200px*4);
    }

    .six{
        left: calc(200px*5);
    }
    .seven{
        left: calc(200px*6);
    }

    .height{
        left: calc(200px*7);
    }
    }

    
    

	

</style>