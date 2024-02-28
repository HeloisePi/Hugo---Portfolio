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
	.seeemore{
		text-decoration: underline;
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
	}
	.contenaireCarousel{
		width: 1800px;
		overflow: hidden;
		display: flex;
		justify-content: center;
		align-items: center;
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
    }

    @media screen and (max-width: 1400px) {
        .contenaireCarousel{
			width: 900px;
		}
    }

    @media screen and (max-width: 1100px) {
        .contenaireCarousel{
			width: 600px;
		}
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