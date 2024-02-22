<script>
	import Experience from "./utilities/Experience.svelte"; 
</script>

<h2>EXPÉRIENCES</h2>
<div class="contenaireExperience" > 


    <!-- //////////////////////////////////////////////////////////// -->
                        <!-- TEMPLATE POUR TES EXPÉRIENCES, TU VAS VOIR C'EST FACILE -->




	<!-- <div class="opacityEffect">        
		<Experience 

		date=     "DATE DE TON EXPERIENCE "                      // N'OUBLIE PAS LES ""
		IntitulePost=     "EXEMPLE:TRÉSORIER"                    // N'OUBLIE PAS LES ""
        >                  
         
		<p>ASSOCIATION BDE MMI</p>                          //ENSUITE TU MET DANS DES BALISES <p>  TOUT TES ÉLÉMENTS 1 PAR 1
		<p>Gestion du budget de l’association</p>


		</Experience>
	</div> -->



    <!-- //////////////////////////////////////////////////////////// -->






	<div class="opacityEffect">
		<Experience 
		date="Mai 2023 - Mai 2024"
		IntitulePost="TRÉSORIER">
		<p>ASSOCIATION BDE MMI</p>
		<p>Gestion du budget de l’association</p>
		</Experience>
	</div>
	<img class="stain stain2"src="/stain/stain2.svg" alt="Tâche">
	<div class="opacityEffect">
		<Experience 
		date="Mai 2023 - Juin 2023"
		IntitulePost="CHARGÉ DE COMMUNICATION">
		<p>VELO-CITE</p>
		<p>Communiquer sur l’événement Tous·tes à vélo</p>
		<p>Animation des réseaux sociaux et de newsletter</p>
		<p>Mise à jour du site internet</p>
		<p>Relation partenaire de l’événement</p>
		</Experience>
	</div>
	<img class="stain stain1" src="/stain/stain1.svg" alt="stain">
	<div class="opacityEffect">
		<Experience 
		date="Juillet 2021 - Août 2021"
		IntitulePost="TÉLÉCONSEILLER">
		<p>CPAM (CONTACT TRACING COVID)</p>
		<p>Gestion des appels téléphoniques  </p>
		<p>Gestion administrative de dossier client</p>
		<p>Formation et tutorat des nouveaux arrivants</p>
		</Experience>
	</div>
	<div class="opacityEffect">
		<Experience 
		date="Octobre 2020 - Juin 2021"
		IntitulePost="EMPLOYÉ POLYVALENT">
		<p>INTERMARCHE</p>
		<p>Gestion de la clientèle</p>
		<p>Gestion de la mise en rayon</p>
		<p>Gestion de la caisse</p>
		<p>Inventaire</p>
		</Experience>
	</div>

	<div class="opacityEffect">
		<Experience 
		date="Juin 2020 - Août 2020"
		IntitulePost="GESTIONNAIRE ADMINISTRATIF">
		<p>CERTEUROPE</p>
		<p>CCréation de certificats électroniques</p>
		<p>Gestion des dossiers internes</p>
		<p>Gestion de la clientèle</p>
		<p>Ouverture et tri de courrier</p>
		</Experience>
	</div>
</div>



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
</style>
