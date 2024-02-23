<script>
	import Experience from "./utilities/Experience.svelte"; 
</script>

<h2>EXPÉRIENCES</h2>
<section class="contenaireExperience" > 


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
		<p>Création de certificats électroniques</p>
		<p>Gestion des dossiers internes</p>
		<p>Gestion de la clientèle</p>
		<p>Ouverture et tri de courrier</p>
		</Experience>
	</div>
</section>



<style>
    .contenaireExperience{
        z-index: 10000;
		margin-bottom: 148px;
    }
</style>