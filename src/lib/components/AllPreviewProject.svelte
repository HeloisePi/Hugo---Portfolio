<script>
import PreviewProject from "./utilities/PreviewProject.svelte";

</script>
<h2>PROJETS</h2>
<section>



    <div class="contenaireProject">
        <PreviewProject
        title="Conviviel"
        description="Réalisation d'un épisode pilote d'une émission fictive"
        srcImg="/project/projet1.png"
        srcImgHover="/project/projet1-hover.png">
        </PreviewProject>
        <PreviewProject
        title="Hors Champs"
        description="Réalisation d’un court métrage de 5 min"
        srcImg="/project/projet2.png"
        srcImgHover="/project/projet2-hover.png">
        </PreviewProject>
        <PreviewProject
        title="Bande dessinée"
        description="Création d’une BD en anglais sur des super héros"
        srcImg="/project/projet3.png"
        srcImgHover="/project/projet3-hover.png">
        </PreviewProject>
        <PreviewProject
        title="Show Time"
        description="Réalisation d'un épisode pilote d'une émission fictive"
        srcImg="/project/projet4.png"
        srcImgHover="/project/projet4-hover.png">
        </PreviewProject>
        <a href="/projets" class="all"><p>Tout découvrir</p></a>
    </div>

</section>


<style>
    .all p{
        text-decoration: underline;
    }

    section{
        padding: 0;
        margin: 0;
        display: flex;
        justify-content: center;
        align-items: center;

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

    }

    @media screen and (max-width: 1180px) {
        .contenaireProject{
            grid-template-columns: 1fr;
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