<script>

</script>

<section id="contact">
    <h2>
        Contact
    </h2>


<a class="contactLink" href="mailto:hugo.mensah@mmibordeaux.com" target="_blank">
    <img src="/icon/mail.svg" alt="Mail" >
    <p>hugo.mensah@mmibordeaux.com</p>
</a>
<a class="contactLink" href="tel:+330778564468" target="_blank">
    <img src="/icon/phone.svg" alt="Mail">
    <p>07 78 56 44 68</p>
</a>
<a class="contactLink" href="https://linkedin.com/in/hugo-mensah" target="_blank">
    <img src="/icon/linkdin.svg" alt="Mail">
    <p>www.linkedin.com/in/hugo-mensah</p>
</a>

<p class="thank">
    Je tiens à vous remercier d'avoir pris le temps de parcourir mon portfolio et de découvrir mes réalisations en tant qu'étudiant en fin de deuxième année du BUT Métiers du Multimédia et de l'Internet. <br>
Enfin, merci à <span class="italic"><a href="https://heloisepingitore.fr" target="_blank">Héloïse PINGITORE</a></span>, d’avoir réalisé le développement de   <span class="italic"><a href="https://www.figma.com/file/Q3wSzofoeja8q9CkTTSSUZ/Portfolio?type=design&node-id=334-160&mode=design">mes maquettes Figma</a></span>  pour ce portfolio  ! N’hésitez pas à aller voir son portfolio juste  <span class="italic"><a href="https://heloisepingitore.fr" target="_blank">ici</a></span> .
</p>

</section>




<style lang="scss">
     @import '../styles/global.scss';
    h2{
        transform: translateX(-110px);
    }

    @media screen and (max-width: 900px) {
        h2{
			transform: translateX(-30px);
		}
		
    }
    #contact{
        margin-left: 110px;
        z-index: 1000;
        z-index: 0;
        padding-top: 181px;

    }



    .contactLink{
        padding-bottom: 65px;
        display: flex;
        align-items: center;
        gap: 117px;
    }

    @media screen and (max-width: 900px) {
        .contactLink{
            flex-direction: column;
            gap: 15px;
        }
        #contact{
        margin-left: 0px;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }


    }

    .thank{
        padding-top: 9rem;
    }

    a,p 
    {
        width: fit-content;
    }

    


</style>