<script>
	import ButtonMore from "./utilities/ButtonMOre.svelte";
import PreviewProject from "./utilities/PreviewProject.svelte";

</script>
<h2>PROJETS</h2>
<section>



    <div class="contenaireProject">
        <PreviewProject
        title="Conviviel"
        description="Réalisation d'un épisode pilote d'une émission fictive"
        src="/projets#Conviviel"
        srcImg="/project/projet1.png"
        srcImgHover="/project/projet1-hover.png">
        </PreviewProject>
        <PreviewProject
        title="Hors Champs"
        description="Réalisation d’un court métrage de 5 min"
        srcImg="/project/projet2.png"
        src="/projets#COURT MÉTRAGE"
        srcImgHover="/project/projet2-hover.png">
        </PreviewProject>
        <PreviewProject
        title="Bande dessinée"
        description="Création d’une BD en anglais sur des super héros"
        srcImg="/project/projet3.png"
        src="/projets#Bande dessinée"
        srcImgHover="/project/projet3-hover.png">
        </PreviewProject>
        <PreviewProject
        title="Show Time"
        description="Réalisation d'un épisode pilote d'une émission fictive"
        src="/projets#SHOW TIME"
        srcImg="/project/projet4.png"
        srcImgHover="/project/projet4-hover.png">
        </PreviewProject>
        
    </div>
    <ButtonMore href="/projets"><p>Tout découvrir</p></ButtonMore>

</section>


<style lang="scss">
     @import '../styles/global.scss';
    a{
        color: #DDD7D0;
		z-index: 0;
        text-decoration: underline;
        width: fit-content;
        &:hover{
            text-decoration: underline;
            
            color: $offWhite;
            p{
                width: fit-content;
                color: #DDD7D0;
                text-decoration: underline;
            }
        }
       
	}
    .contenaireProject p{
                width: fit-content;
                color: #DDD7D0;
                text-decoration: none;
                &:hover{
                    color: #DDD7D0;
                }
    }


    .all p{
        text-decoration: underline;
    }

    section{
        padding: 0;
        margin: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 2;
        flex-direction: column;

    }
    .contenaireProject{
        display: grid;
        padding: 110px;
        grid-template-columns:  1fr 1fr;
        grid-template-rows:  1fr 1fr;
        row-gap: 20px;
        column-gap: 20px;
        width: min-content;
        height: min-content;
        align-items: center;
        justify-items: center;
        z-index: 5;

    }

    @media screen and (max-width: 1180px) {
        .contenaireProject{
            grid-template-columns: 1fr;
            grid-row: 1fr 1fr 1fr 1fr;
            margin-bottom: 100px;
            padding: 0px;
            gap: 8rem;
        }
}
@media screen and (max-width: 616px) {
         .contenaireProject{
            gap: 5rem;
            column-gap: 0px;
            
        }

}


</style>