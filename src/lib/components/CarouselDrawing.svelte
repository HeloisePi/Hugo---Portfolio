<script>
	import Carousel from "./utilities/Carousel.svelte";


</script>

<h2>Dessin</h2>
<section>
	<div class="contenaireCarousel">
		<Carousel></Carousel>
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
			width: 400px;
		}
		
    }

	@media screen and (max-width: 475px) {
        .contenaireCarousel{
			width: 267px;
		}
    }
	

</style>