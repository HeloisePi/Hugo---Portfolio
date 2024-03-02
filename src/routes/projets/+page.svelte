<script>

    import MiniCarousel from '$lib/components/utilities/MiniCarousel.svelte';
import Projects from '$lib/components/utilities/Projects.svelte'; 
    import { onMount, onDestroy } from 'svelte';
    import { writable, get } from 'svelte/store';

    let tags = [];
    const selectedTags = writable([]);
    const filtersWidth = writable(100); // initial width of filters

    selectedTags.subscribe(value => {
        filterProjects(value);
    });

    function isChecked(tag) {
        const selectedTagsArray = get(selectedTags);
        return selectedTagsArray.includes(tag);
    }

    function extractTagsFromHTML() {
        let extractedTags = [];
        let projectDivs = document.querySelectorAll('.contenaire');
        projectDivs.forEach(div => {
            let projectTags = div.querySelectorAll('.tag p');
            projectTags.forEach(tag => {
                extractedTags.push(tag.textContent.trim());
            });
        });
        return Array.from(new Set(extractedTags));
    }

    function filterProjects(selectedTags) {
        if (selectedTags.length === 0) {
            document.querySelectorAll('.contenaire').forEach(container => {
                container.style.display = 'block';
            });
            return;
        }
        let projectContainers = document.querySelectorAll('.contenaire');
        projectContainers.forEach(container => {
            let tagsInContainer = Array.from(container.querySelectorAll('.tag p')).map(tag => tag.textContent.trim());
            let showContainer = selectedTags.some(tag => tagsInContainer.includes(tag));
            container.style.display = showContainer ? 'block' : 'none';
        });
    }

    function handleTagSelection(tag, event) {
        const checked = event.target.checked;
        const label = event.target.parentNode; // Récupérer le parent (le label)
        const img = label.querySelector('img');

        // Appliquer les styles directement au label en fonction de l'état checked
        if (checked) {
            img.style.display = "block";
            label.style.backgroundColor = '#9C528B';
            label.style.width= "fit-content";
        } else {
            // Remettre les styles par défaut si la case est décochée
            img.style.display = "none";
            label.style.backgroundColor = '';
        }

        // Mettre à jour les tags sélectionnés dans le store
        if (checked) {
            selectedTags.update(tags => [...tags, tag]);
        } else {
            selectedTags.update(tags => tags.filter(t => t !== tag));
        }
    }

    onMount(() => {
        tags = extractTagsFromHTML();
    });

    onDestroy(() => {
        // cleanup code here if needed
    });

    function toggleFiltersWidth() {
        const filters = document.querySelector('.filters');
        const filter = filters.querySelector('.filter');
        const img = filters.querySelector('.expand'); // Ajoutez des guillemets autour de 'img'
        console.log('filtres', filters);
        filters.classList.toggle('open');
        if (filters.classList.contains('open')) {
            filter.style.transform = ""
            img.style.position = "absolute";
            img.style.right = "0";
            filters.style.width = " fit-content";
            filters.style.height = "fit-content";
            img.style.transform = "rotate(182deg)";
        } else {
            filter.style.transform = "translateX(43px)"
            img.style.position = "";
            filters.style.height = "56px";
            img.style.transform = "rotate(0deg)";
            filters.style.width = '116px';
        }
}
</script>
<div class="relative">
    <section>
        <h1>Projects</h1>
        </section>
    <div class="contenaireStain secondContenaireStain">
        <img class="stain stain1" src="/stain/stain1.svg" alt="tâche">
        <img class="stain stain2" src="/stain/stain2.svg" alt="tâche">
        <img class="stain stain3" src="/stain/stain3.svg" alt="tâche"> 
    </div>
</div>



<main>
    <div class="contenairefilters">

    
    <div class="filters" style="width: {get(filtersWidth)}px" on:click={toggleFiltersWidth}>
        <h3>Filtre :</h3>
        <img class="expand" src="/icon/expand_more.svg" alt="expand more">
        <div class="filter">
        {#each tags as tag}
            <label class="tag-label">
                <input type="checkbox" on:change={(event) => handleTagSelection(tag, event)} checked={isChecked(tag)} value={tag}>
                <img src="/icon/check.svg" alt="check">
                <div class="tag">
                    <div class="color" style="background-color: {tag === 'AUDIOVISUEL' ? '#0A12C2' : (tag === 'DESIGN' ? '#C20ABA' : (tag === 'ÉCRITURE' ? '#C20A0A' : (tag === 'DÉVELOPPEMENT' ? '#C25A0A' : '')))}"></div>
                    <p style="color: {tag === 'AUDIOVISUEL' ? '#0A12C2' : (tag === 'DESIGN' ? '#C20ABA' : (tag === 'ÉCRITURE' ? '#C20A0A' : (tag === 'DÉVELOPPEMENT' ? '#C25A0A' : '')))}">{tag}</p>
                </div>
            </label>
        {/each}
    </div>
    </div>

</div>
    

    <Projects
    title1="Conviviel"
    title2= "Flop!Edt"
    link= "https://www.figma.com/file/Kb4mMIyTzWmDbMsrvZ8OLS/Refonte-Flop!Edt?type=design&node-id=199%3A2117&mode=design&t=WrcwC3MBNgDR1rRc-1"
    linkTitle= "Lien Figma"
    description= "Au cours d'un projet de deux semaines sur l'UX/UI design, j'ai collaboré avec mon groupe pour repenser le gestionnaire d'emploi du tempsFlop!Edt. La première semaine était dédiée à la recherche utilisateur pour comprendre les besoins et les frustrations des utilisateurs, tandis que la deuxième était consacrée à la conception et à l'itération des solutions. Nous avons identifié les lacunes du système existant et élaboré des wireframes détaillés, puis des maquettes interactives. Ce projet m'a permis de maîtriser le processus d'UX/UI design et de développer mes compétences sur Figma."
    tag1= "AUDIOVISUEL"
    tag1Color= "#0A12C2"
    tag2="DESIGN"
    tag2Color= "#C20ABA"
    >
    <MiniCarousel>
            <img class="carouselImage one" src="/project/PageProject/convivial/1.jpg" alt="">
            <img class="carouselImage two" src="/project/PageProject/convivial/2.jpg" alt="">
            <img class="carouselImage thee" src="/project/PageProject/convivial/3.jpg" alt="">
            <img class="carouselImage four" src="/project/PageProject/convivial/4.jpg" alt="">
            <img class="carouselImage five" src="/project/PageProject/convivial/5.jpg" alt="">
            <img class="carouselImage six" src="/project/PageProject/convivial/6.jpg" alt="">
    </MiniCarousel>
    </Projects>


    <Projects
    title1="COURT MÉTRAGE"
    title2= "Hors  Champs"
    link= "https://www.figma.com/file/Kb4mMIyTzWmDbMsrvZ8OLS/Refonte-Flop!Edt?type=design&node-id=199%3A2117&mode=design&t=WrcwC3MBNgDR1rRc-1"
    linkTitle= "Regarder le court métrage"
    description= "'Hors champs' était un projet d'audiovisuel de deux semaines, où nous devions réaliser un court métrage en groupe de cinq personnes, avec un genre imposé. Notre groupe a été assigné au genre 'Buddy Comedy RoadTrip'.
    Durant ce projet, nous avons dû créer une affiche de film, un site vitrine, ainsi qu'un making-of. Cette expérience m'a offert une première occasion de me lancer dans l'acting et m'a permis de développer mes compétences en écriture et en motion design en réalisant le générique du film."
    tag1= "AUDIOVISUEL"
    tag1Color= "#0A12C2"
    tag2="DESIGN"
    tag2Color= "#C20ABA"
    >
    <iframe width="90%" height="300px" src="https://www.youtube.com/embed/T0OiTC6awZA?si=E0HaU-eKt42zPcdC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
    </Projects>
    <Projects
    title1="BanDe dessinée"
    title2= "Against my side"
    link= "https://www.figma.com/file/Kb4mMIyTzWmDbMsrvZ8OLS/Refonte-Flop!Edt?type=design&node-id=199%3A2117&mode=design&t=WrcwC3MBNgDR1rRc-1"
    linkTitle= "Lien Figma"
    description= "Lors de ce devoir en binôme, nous avons été chargés d'écrire et de créer une bande dessinée en anglais. Nous avons commencé par élaborer des personnages, une histoire et un scénario pour notre bande dessinée. Nous avons ensuite travaillé ensemble pour créer les dessins et les dialogues qui allaient être utilisés. Nous avons essayé de faire preuve de créativité tout en nous assurant que notre anglais était correct et facile à comprendre. Ensuite nous avons réalisé tous les dessins, grâce à l'application Procreate."
    tag1= "ÉCRITURE"
    tag1Color= "#C20A0A"
    tag2="DESIGN"
    tag2Color= "#C20ABA"
    >
    <MiniCarousel>
        <img class="carouselImage one" src="project/PageProject/bd/1.jpg" alt="">
        <img class="carouselImage two" src="/project/PageProject/bd/2.png" alt="">
        <img class="carouselImage thee" src="/project/PageProject/bd/3.png" alt="">
        <img class="carouselImage four" src="/project/PageProject/bd/4.png" alt="">
        <img class="carouselImage five" src="/project/PageProject/bd/5.png" alt="">
        <img class="carouselImage six" src="/project/PageProject/bd/6.png" alt="">
    </MiniCarousel>

    </Projects>

    <Projects
    title1="SHOW TIME"
    title2= "Dans ta serre"
    link= "https://www.youtube.com/watch?v=c4llM-dEMJw"
    linkTitle= "Regarder l'épisode"
    description= "Le projet Show Time consistait à créer un épisode pilote pour une émission télévisée fictive intitulée 'Dans ta serre', mettant en avant la nature et l'environnement. Notre équipe a élaboré un scénario, puis a réalisé le tournage en concevant les décors, les costumes et en recrutant les acteurs. J'ai personnellement contribué en utilisant mes compétences en motion design pour créer le générique ainsi que les transitions. De plus, j’ai réalisé des visuels et aidé au montage. "
    tag1= "AUDIOVISUEL"
    tag1Color= "#0A12C2"
    tag2="DESIGN"
    tag2Color= "#C20ABA"
    >
    <iframe width="90%" height="400px" src="https://www.youtube.com/embed/c4llM-dEMJw?si=cpwkIs9pSpB_F6AG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
    </Projects>


    <Projects
    title1="WORKSHOP"
    title2= "Horo Hiro"
    link= "https://www.horohiro.org/"
    linkTitle= "Lien du site"
    description= "Horo Hiro est un projet réalisé avec huit autre étudiants MMI de l'IUT Bordeaux Montaigne, visant à sensibiliser les jeunes à la scoliose et à briser les tabous autour du port du corset orthopédique. Constatant un manque d'accompagnement pour ces jeunes, on a souhaité offrir une solution positive en redéfinissant le corset comme un accessoire à valoriser. Pour ce faire, on a fait appel à des artistes pour créer des designs innovants, proposer des témoignages sur notre site web et mettre en place une communauté en ligne pour partager expériences et soutien mutuel."
    tag1= "AUDIOVISUEL"
    tag1Color= "#0A12C2"
    tag2="DESIGN"
    tag2Color= "#C20ABA"
    >
    <MiniCarousel>
        <img class="carouselImage one" src="project/PageProject/WORKSHOP/1.jpg" alt="">
        <img class="carouselImage two" src="/project/PageProject/WORKSHOP/2.jpg" alt="">
        <img class="carouselImage thee" src="/project/PageProject/WORKSHOP/3.jpg" alt="">
        <img class="carouselImage four" src="/project/PageProject/WORKSHOP/4.jpg" alt="">
        <img class="carouselImage five" src="/project/PageProject/WORKSHOP/5.jpg" alt="">
        <img class="carouselImage six" src="/project/PageProject/WORKSHOP/6.jpg" alt="">
    </MiniCarousel>
    </Projects>

    <Projects
    title1="Employabilité"
    title2= "Cv Vidéo"
    link= "https://youtu.be/-JUKu1lUfOQ"
    linkTitle= "Regarder le motion design"
    description= "Le projet Employabilité avait pour objectif de nous préparer au monde professionnel, en nous offrant des ateliers et des formations sur les compétences professionnelles, la rédaction de CV et de lettres de motivation, ainsi que la préparation aux entretiens d'embauche. Un moment fort du projet a été la réalisation d'un court CV vidéo, où nous avons pu présenter de manière concise et créative nos parcours aux potentiels employeurs. Cette expérience nous a permis de développer notre confiance en nous et de comprendre l'importance de la communication dans le monde du travail. "
    tag1= "AUDIOVISUEL"
    tag1Color= "#0A12C2"
    >
    <iframe width="90%" height="400px" src="https://www.youtube.com/embed/-JUKu1lUfOQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
    </Projects>





    <Projects
    title1="Ruby on rails"
    title2= "M’OG"
    link= "https://mog-mog.osc-fr1.scalingo.io/"
    linkTitle= "Lien du site"
    description= "Ce projet en binôme m'a offert l'opportunité d'apprendre le langage Ruby on Rails. Notre objectif était de créer un site internet, et nous avons opté pour un blog recensant des super héros. Nous avons commencé par concevoir des maquettes sur Figma pour visualiser le design du site. Ensuite, nous avons créé des fiches personnages détaillées, contenant des informations pertinentes sur les super héros sélectionnés. Grâce à Midjourney, nous avons également généré des images pour illustrer ces personnages. "
    tag1= "DESIGN"
    tag1Color= "#C20ABA"
    tag2="DÉVELOPPEMENT"
    tag2Color= "#C25A0A"
    
    >
    <MiniCarousel>
        <img class="carouselImage one" src="project/PageProject/ruby/1.jpg" alt="">
        <img class="carouselImage two" src="/project/PageProject/ruby/2.jpg" alt="">
        <img class="carouselImage thee" src="/project/PageProject/ruby/3.jpg" alt="">
       
    </MiniCarousel>
    </Projects>




    <Projects
    title1="Théorie animée"
    title2= "Théorie de David Perkins "
    link= "https://www.youtube.com/watch?v=Wrts3Bk6khw"
    linkTitle= "Regarder le motion design"
    description= "Ce projet était un travail en binôme visant à vulgariser la théorie de David PERKINS sur l'individu solo et l'individu plus. Cette théorie distingue deux modes de pensée : le mode ‘solo’, où l'individu résout des problèmes seul, et le mode ‘plus’, favorisant la coopération pour résoudre des problèmes complexes. Notre objectif était de rendre cette théorie accessible à tous via un motion design explicatif. Nous avons utilisé les codes du motion design pour créer une vidéo claire et attrayante."
    tag1= "AUDIOVISUEL"
    tag1Color= "#0A12C2"
    tag2="DESIGN"
    tag2Color= "#C20ABA"
    tag3= "ÉCRITURE"
    tag3Color= "#C20A0A"

    >
    <iframe width="90%" height="400px" src="https://www.youtube.com/embed/Wrts3Bk6khw?si=3Lmk1DOO9RRXm6Gu" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
    </Projects>





    <Projects
    title1="Bacchanight"
    title2= "Maria"
    link= "https://maria-bacchanight.netlify.app/"
    linkTitle= "Lien du site"
    description= "Ce projet, est en partenariat avec le MusBa pour la Bacchanight 2024. Nous avons créé une histoire interactive avec les tableaux du musée. Notre groupe étions sur la période du siècle d’or hollandais. Nous avons effectué des recherches approfondies sur ce mouvement, pour réaliser une histoire fictive cohérente. Pendant ce projet, j’ai réalisé des visuels et des illustrations."
    tag1= "ÉCRITURE"
    tag1Color= "#C20A0A" 
    >
    <MiniCarousel>
        <img class="carouselImage one" src="project/PageProject/bacchanight/1.jpg" alt="">
        <img class="carouselImage two" src="/project/PageProject/bacchanight/2.jpg" alt="">
        <img class="carouselImage thee" src="/project/PageProject/bacchanight/3.jpg" alt="">
        <img class="carouselImage four" src="/project/PageProject/bacchanight/4.jpg" alt="">
       
    </MiniCarousel>
    </Projects>






    <Projects
    title1="Économie numérique"
    title2= " Infographies Darwin et Ammi"
    description= "Le projet consistait à créer deux infographies : une sur l'écosystème de Darwin à Bordeaux et une autre sur la start-up Briofood, active dans cet écosystème. Pour la première infographie, nous avons effectué des recherches approfondies sur Darwin, identifiant ses entreprises clées. La seconde infographie s'est concentrée sur Briofood, notamment sur leur produit Ammi et leur impact dans l’écosystème de Darwin. Ce projet nous a permis d’avoir un aperçu du monde des start-ups et de l'importance des écosystèmes locaux."
    tag1= "DESIGN"
    tag1Color= "#C20ABA" 
    >
    <MiniCarousel>
        <img class="carouselImage one" src="project/PageProject/infographie/1.jpg" alt="">
        <img class="carouselImage two" src="/project/PageProject/infographie/2.jpg" alt="">
       
    </MiniCarousel>
    </Projects>


</main>

<style lang="scss">

    .carouselImage{
        position: absolute;
        left: 0;
        top: 0;
        width: 480px;
        height: 100%;
        object-fit: contain;
    }
    .one{
        left : 0;
    }

    .two{
        left : 480px;
    }

    .thee{
        left : calc(480px*2);
    }
    .four{
        left : calc(480px*3);
    }

    .five{
        left : calc(480px*4);
    }

    .six{
        left: calc(480px*5);
    }

    .seven{
        left: calc(480px*6);
    }

    .height{
        left: calc(480px*7);
    }


    @media screen and (max-width: 635px) {
        .carouselImage{
            width: 300px;
        }
        .two{
        left : 300px;
    }

    .thee{
        left : calc(300px*2);
    }
    .four{
        left : calc(300px*3);
    }

    .five{
        left : calc(300px*4);
    }

    .six{
        left: calc(300px*5);
    }
    .seven{
        left: calc(300px*6);
    }

    .height{
        left: calc(300px*7);
    }
    }





    .filter{
        width: 900px;
        display: flex;
        align-items: center;
        justify-content: space-around;
        transform: translateX(43px);
    }

    @media screen and (max-width: 730px) {
        .filter{
            
            flex-direction: column;
            gap: 20px;
            width: fit-content;
        }
        .contenairefilters .filters{
            width: fit-content;
            flex-direction: column;
            align-items: flex-start;
            width: 116px;
            height: 56px;

            .expand{
                position: absolute;
                top: 21px;
            }
           
        }

    }

    .contenairefilters{
        width: 100%;
    }

    h1{
        animation: open 3s ease infinite;
    }


    .filters {
        display: flex;
        align-items: center;
        border: 2px solid #DDD7D0;
        border-radius: 20px;
        padding: 11px;
        // width: fit-content;
        gap: 20px;
        width: 160px;
        overflow: hidden;
        transition: width 1s ease-in-out;
        position: relative;

        /* Animation appliquée à .filters */
        
}

.filters .expand {
    width: 35px;
    height: 17px;
    position: absolute;
    right: -5px;
}

.filters h3 {
    white-space: nowrap;
}

/* Définition de l'animation */
@keyframes filterOpen { 
    0% {
        width: 116px;
    }
    90% {
        width: 40%;
    }
    100% {
        width: fit-content;
    }
}

@keyframes close{
    0%{
        width: fit-content;
    }

    75%{
        
        width: 100px;
    
    }

    100%{
        width: 116px;
    }
}

    label {

    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: row;
    border-radius: 10px;
    width: fit-content;
    height: auto;
    padding: 4px;
    gap: 4px;
    transition: 0.25s ease-in-out;
        img{
            transition: 0.25s ease-in-out;
            display: none;
        width: 32px;
        height: 17px;

    }
    }
    


.tag {
    background-color: #E8E8E8;
    border-radius: 10px;
    padding: 0.5rem;
    display: flex;
    align-items: center;
    width: fit-content;
    height: 30px;
}

.tag .color {
    width: 15px;
    height: 15px;
    border-radius: 50%;
    /* Utilisez une couleur spécifique au lieu de var(--tag1Color) car --tag1Color n'est pas défini dans le CSS que vous avez fourni */
    background-color: #000; /* Par exemple */
    margin-right: 0.5rem;
}

// ----------------------------------------------------------------
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

section{
        /* position: absolute; */
        /* top: 0; */
        /* height: 190vh; */
        height: 100vh; 
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        gap: 1rem;
        position: relative;
        width: 100%;
        overflow: hidden;
        z-index: 0;
    }

    main{
		padding: 110px;
        gap: 124px;
		padding-top: 5rem ;
        padding-bottom: 5rem;
		width: 100vw;
		overflow-x: hidden;
		display: flex;
		flex-direction: column;
        align-items: center;
		margin-bottom: 148px;
		margin-bottom: 234px;
        z-index: 0;
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

    @media screen and (max-height: 1000px) {
                section h1{
                    font-size: 48px;
                }
                h2{
                    font-size: 28px;
                }
                section .scroll{
                    width: 70px;
                    margin-top: 0px;
                    
                }
                section .arrow{
                    width: 15px;
                    height: auto;
                }

            }
            @media screen and (max-height: 500px) {
                section{
                    gap: 0;
                }
                h2{
                    margin-bottom: 40px;
                }
            }
    

</style>