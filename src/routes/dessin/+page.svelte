<script>
	import Hero from "$lib/components/Hero.svelte";
import CarouselPageDessin from "$lib/components/utilities/CarouselPageDessin.svelte";

</script>

    <div class="contenaireStain">
        <img class="stain stain1" src="/stain/stain1.svg" alt="tâche">
        <img class="stain stain2" src="/stain/stain2.svg" alt="tâche">
        <img class="stain stain3" src="/stain/stain3.svg" alt="tâche"> 
    </div>
<Hero
title="DESSINS">
</Hero>
<main>
<CarouselPageDessin 
title="Portrait">
    <img src="/dessin/femme_blonde.jpg" alt="femme_blonde">
    <img src="/dessin/femme_profil.jpg" alt="femme_profil">
    <img src="/dessin/femme_face.jpg" alt="femme face">
</CarouselPageDessin>

<CarouselPageDessin 
title="Personnage">
    <img src="/dessin/Nebula.jpg" alt="Nebula">
    <img src="/dessin/Wednesday.jpg" alt="Wednesday">
    <img src="/dessin/Max.jpg" alt="Max">
    <img src="/dessin/Scarlet_Witch.jpg" alt="Scarlet_Witch">
    <img src="/dessin/Wanda.jpg" alt="Wanda">
</CarouselPageDessin>


<CarouselPageDessin 
title="Abstrait">
    <img src="/dessin/femme_poignardee.jpg" alt="femme_poignardee">
    <img src="/dessin/oeil_ombre.jpg" alt="oeil_ombre">
    <img src="/dessin/homme_ombre.jpg" alt="homme_ombre">
    <img src="/dessin/personne_depresed.jpg" alt="personne_depresed">
    <img src="/dessin/homme_seul.jpg" alt="homme_seul">
</CarouselPageDessin>

<CarouselPageDessin 
title="Divers">
    <img src="/dessin/arbre.jpg" alt="arbre">
    <img src="/dessin/super_heros.jpg" alt="super_heros">

</CarouselPageDessin>
</main>


<style>
    	.stain{
        position: absolute;
        z-index: 0;
        filter: blur(378.28px);
    }

    .stain1{
        left: 0;
        transform: translate(-50vw, 12vh);
        animation: RotateStain1 10s linear infinite; 
        width: 80%;

    }

    .stain2{
        right: 0;
        transform: translate(32rem, -52vh);
        animation: RotateStain2 15s linear infinite; 
        width: 50%;
    }

    .stain3{
        width: 72%;
        transform: translate(6vw, 1vh);
        width: 60%;
    }


    @keyframes RotateStain1{
        0%{
            transform: translate(-66vw, 3vh);
        }

        35%{
            transform: translate(-48vw, 36vh);
        }

        65%{
            transform: translate(-35vw, 0vh);
        }

        100%{
            transform:translate(-66vw, 3vh);
        }
    }

    @keyframes RotateStain2{
        0%{
            transform: translate(30vw, -30vh);
        }

        35%{
            transform: translate(30vw, 11vh);
        }

        65%{
            transform: translate(17vw, -16vh);
        }

        100%{
            transform: translate(30vw, -30vh);
        }
    }
    .contenaireStain{
		position: absolute;
		overflow: hidden;
		width: 100vw;
		height: fit-content;
		min-height: 200vh;
		top: 0;
		left: 0;
		width: 100vw;
	}

    img{
        height: 450px;
        width: fit-content;
        object-fit: cover;
    }


    main{
		padding: 0px;
		padding-bottom: 0;
        gap: 234px;
		padding-top: 0 ;
		width: 100vw;
		overflow-x: hidden;
		display: flex;
		flex-direction: column;
		margin-bottom: 148px;
		margin-bottom: 234px;
	}
	@media screen and (max-width: 900px) {
        main{
			padding: 30px;
		}
		
    }

	.contenaireStain{
		position: absolute;
		overflow: hidden;
		width: 100vw;
		height: fit-content;
		min-height: 200vh;
		top: 0;
		left: 0;
		width: 100vw;
        padding: 20vh;
	}


</style>