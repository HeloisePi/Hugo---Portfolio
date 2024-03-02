<script>
	import Hero from "$lib/components/Hero.svelte";

</script>


    <div class="contenaireStain">
        <img class="stain stain1" src="/stain/stain1.svg" alt="tâche">
        <img class="stain stain2" src="/stain/stain2.svg" alt="tâche">
        <img class="stain stain3" src="/stain/stain3.svg" alt="tâche"> 
    </div>


    <div class="contenaireStain">
        <img class="stain stain1" src="/stain/stain1.svg" alt="tâche">
        <img class="stain stain2" src="/stain/stain2.svg" alt="tâche">
        <img class="stain stain3" src="/stain/stain3.svg" alt="tâche"> 
    </div>
<Hero
title="Mentions légales"></Hero>


<main>
    <p>Adresse e-mail : hugo.mensah@mmibordeaux.com <br>
        Numéro de téléphone : +33 7 78 56 44 68 <br>
        Hébergement : Netlify <br>
        Adresse : Bordeaux</p>

    <h3>Propriété intelectuelle</h3>
    <p>Tous les éléments présents sur le site (photographie, logo, illustration, dessin) sont protégés par la loi en vigueur au titre de la propriété intellectuelle.<br>
        En effet toute reproduction ou utilisation est strictement interdite sans accord au préalable de l'éditeur.<br>
        La reproduction et la copie des contenus par l'utilisateur requièrent une autorisation préalable du site. Dans ce cas, toute utilisation à des usages commerciaux ou à des fins publicitaires est proscrite.</p>
        <h3>
            Champ d’application / contenu utilisateur
        </h3>
        <p>
            Description des services : Ce site propose un service non-marchand. <br>
            Le service proposé pour les utilisateurs est de participer à une histoire interactive. <br>
            Le site est accessible gratuitement depuis n’importe où par tout utilisateur disposant d’un accès à Internet.<br>
            Tous les frais nécessaires pour l’accès aux services (matériel informatique, connexion Internet…) sont à la charge de l’utilisateur.<br>
            Pour des raisons de maintenance ou autres, l’accès au site peut être interrompu ou suspendu par l’éditeur sans préavis ni justification.<br>
        </p>
        <h3>
            Responsabilité
        </h3>
        <p>Les informations diffusées sur ce portfolio sont présentées à titre purement informatif et sont sans valeur contractuelle. En dépit des mises à jour, la responsabilité du site ne peut être engagée en cas de modification des dispositions administratives et juridiques apparaissant après la publication.<br>
            Le site décline toute responsabilité concernant les éventuels virus pouvant infecter le matériel informatique de l'utilisateur après l’utilisation ou l’accès à ce site. <br>
            Le site ne peut être tenu pour responsable en cas de force majeure ou du fait imprévisible et insurmontable d’un tiers.</p>
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
        width: auto;
    }
    main{
		padding: 110px;
		padding-bottom: 0;
        gap: 21px;
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