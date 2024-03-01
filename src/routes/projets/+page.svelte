<script>

    import Projects from '$lib/components/utilities/Projects.svelte'; 
    import { writable, get } from 'svelte/store';
    import { onMount } from 'svelte';

    let tags = [];
    const selectedTags = writable([]);

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
        img.style.opacity = "1";
        label.style.backgroundColor = '#9C528B';
        label.style.display = 'flex';
        label.style.justifyContent = 'flex-start';
        label.style.alignItems = 'center';
        label.style.flexDirection = 'row';
        label.style.borderRadius = '10px';
        label.style.width = 'fit-content';
        label.style.height = 'auto';
        label.style.padding = '4px';
    } else {
        // Remettre les styles par défaut si la case est décochée
        img.style.opacity = "0";
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
</script>

<h1>Projects</h1>

<div class="filters">
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

    label {

        display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: row;
    border-radius: 10px;
    width: fit-content;
    height: auto;
    padding: 4px;
        img{
        opacity: 0;
        width: 32px;
        height: 32px;

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