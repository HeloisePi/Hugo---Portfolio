<script>
    import { writable, get } from 'svelte/store';

    import { onMount } from 'svelte';
	import Projects from '$lib/components/utilities/Projects.svelte';

    // Liste des tags uniques disponibles
    let tags = [];

    // Variable réactive pour stocker les tags sélectionnés par l'utilisateur
    const selectedTags = writable([]);

    // Souscription à la variable selectedTags pour déclencher la fonction de filtrage lorsqu'elle est mise à jour
    selectedTags.subscribe(value => {
        filterProjects(value);
    });

    function isChecked(tag) {
    const selectedTagsArray = get(selectedTags); // Obtenez la valeur actuelle des tags sélectionnés
    return selectedTagsArray.includes(tag);
}

    // Fonction pour extraire les tags du HTML
    function extractTagsFromHTML() {
        let extractedTags = [];
        // Sélectionnez les balises div contenant des informations sur les projets
        let projectDivs = document.querySelectorAll('.contenaire');
        // Parcourez chaque balise div
        projectDivs.forEach(div => {
            // Récupérez les tags de cette balise div
            let projectTags = div.querySelectorAll('.tag p');
            // Ajoutez les tags à la liste des tags extraits
            projectTags.forEach(tag => {
                extractedTags.push(tag.textContent.trim());
            });
        });
        // Retournez les tags extraits uniques
        return Array.from(new Set(extractedTags));
    }

    function filterProjects(selectedTags) {
    // Si aucun tag n'est sélectionné, afficher tous les conteneurs
    if (selectedTags.length === 0) {
        document.querySelectorAll('.contenaire').forEach(container => {
            container.style.display = 'block';
        });
        return;
    }

    // Sélectionnez tous les conteneurs de projet
    let projectContainers = document.querySelectorAll('.contenaire');
    // Parcourez chaque conteneur
    projectContainers.forEach(container => {
        // Vérifiez si le conteneur possède au moins un des tags sélectionnés
        let tagsInContainer = Array.from(container.querySelectorAll('.tag p')).map(tag => tag.textContent.trim());
        let showContainer = selectedTags.some(tag => tagsInContainer.includes(tag));
        // Affichez ou masquez le conteneur en fonction du résultat
        container.style.display = showContainer ? 'block' : 'none';
    });
}

    // Utilisez writable pour créer une variable réactive pour chaque tag
    const tagStates = {};

    function handleTagSelection(tag, event) {
    const checked = event.target.checked; // Accédez directement à la propriété checked
    if (checked) {
        selectedTags.update(tags => [...tags, tag]);
    } else {
        selectedTags.update(tags => tags.filter(t => t !== tag));
    }
}

    onMount(() => {
        // Exécute la fonction d'extraction des tags une fois que le composant est monté
        tags = extractTagsFromHTML();
        // Crée une variable réactive pour chaque tag
        tags.forEach(tag => {
            tagStates[tag] = writable(false);
        });
    });
</script>

<h1>Projects</h1>

<!-- Interface utilisateur pour les filtres -->
<div class="filters">
    {#each tags as tag}
        <label>
            <!-- Utilisation de la variable réactive correspondant à chaque tag -->
            <input type="checkbox" on:change={(event) => handleTagSelection(tag, event)} checked={isChecked(tag)} value={tag}>

            {tag}
        </label>
    {/each}
</div>
<main>
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
        <img src="/portrait.png" alt="test">
        </Projects>
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
        <img src="/portrait.png" alt="test">
        </Projects>
        <Projects
        title1="Conviviel"
        title2= "Flop!Edt"
        link= "https://www.figma.com/file/Kb4mMIyTzWmDbMsrvZ8OLS/Refonte-Flop!Edt?type=design&node-id=199%3A2117&mode=design&t=WrcwC3MBNgDR1rRc-1"
        linkTitle= "Lien Figma"
        description= "Au cours d'un projet de deux semaines sur l'UX/UI design, j'ai collaboré avec mon groupe pour repenser le gestionnaire d'emploi du tempsFlop!Edt. La première semaine était dédiée à la recherche utilisateur pour comprendre les besoins et les frustrations des utilisateurs, tandis que la deuxième était consacrée à la conception et à l'itération des solutions. Nous avons identifié les lacunes du système existant et élaboré des wireframes détaillés, puis des maquettes interactives. Ce projet m'a permis de maîtriser le processus d'UX/UI design et de développer mes compétences sur Figma."
        tag1= "ÉCRITURE"
        tag1Color= "#C20A0A"

        >
        <img src="/portrait.png" alt="test">
        </Projects>
</main>


<style lang="scss">

label{
    color: white;
}

input{
    border-color: white;
    border-color: white;
    height: 50px;
    width: 50px;
    background-color: white;
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
    }

    main{
		padding: 110px;
        gap: 21px;
		padding-top: 5rem ;
        padding-bottom: 5rem;
		width: 100vw;
		overflow-x: hidden;
		display: flex;
		flex-direction: column;
        align-items: center;
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