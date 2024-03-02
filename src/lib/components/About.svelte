<section>

    <div class="hugoFace">
       <img class="portrait" src="/portrait.png" alt="portrait">
      <div class="contenaireGif">
            <img class="gif" src="/cat.gif" alt="Gif de chat qui fait coucou">
        </div>
    </div>

    <div class="text">
        <h3>Je m’appelle Hugo, j’ai 21 ans. </h3>
        <p>Actuellement en BUT MMI (Métiers du Multimédia et de l’Internet) à l’IUT de Bordeaux Montaigne. Je suis à la recherche d’un stage et d'une alternance dans l'UX/UI ou dans l'audiovisuel. Passionné par le monde de la création et des nouvelles technologies, je suis constamment à la recherche de nouvelles façons de m’exprimer et de créer. 
            Durant mon temps libre j’aime dessiner, faire de l’escalade et apprendre la guitare.</p>
    </div>
</section>



<style lang="scss">
    @import '../styles/global.scss';
    section{
        width: 100%;
        z-index: 1000;
        height: 100vh;
        display: grid;
        grid-template-columns: 50% 50%;
        align-items: center;
        justify-items: center;
        z-index: 0;
    }

    .hugoFace{
        position: relative;
        width: 370px;
    }

    .gif{
        transform: rotate(20deg);
        width: 224.18px;
        height: auto;
        transition:  0.25s ease-in;
        // // opacity: 0;
    }


    h3, p{
        width: 100%;
    }

    .text{
        max-width: 900px;
        width: 100%;
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }



    .portrait{
    
        width: 100%;
        z-index: 100;
        position: relative;
    }

    .contenaireGif{
        position: absolute;
        left: 9%;
        top: 14%;
        transition:  transform 0.25s ease-in;
        transform: translate(0rem, 0rem);
    }

    .hugoFace{
        position: relative;
        transition: transform 0.25s ease-in;
        &:hover{
            transform: translate(-3rem, 3rem);
            .contenaireGif{
                transform: translate(10rem, -7rem);
                animation:  cat 5s ease;
                    
                 }
            }
    }


         @media screen and (max-width: 530px) {
             .hugoFace {
                width: 214px;

                &:hover .contenaireGif{
                    transform: translate(5rem, -5rem);
                }
             }

             .gif{
                width: 141.18px;
             }

             
         }

         @media screen and (max-width: 1100px) {
         section{
           grid-template-columns: 1fr;
         }
         }
    

</style>