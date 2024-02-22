<script lang="ts">
	import { onMount, type ComponentType } from 'svelte';
	import cn from 'clsx';

	import { lenisStore as lenis } from '$lib/stores/lenis';
	import { introOutStore } from '$lib/stores/introOut';
	import { addThreshold } from '$lib/stores/thresholds';
	import { setThemeStore, themeStore } from '$lib/stores/theme';
	import {
		homePageLoadedComponentsStore,
		setHomePageLoadedComponentsStore
	} from '$lib/stores/homePageLoadedComponents';

	import { intersection } from '$lib/actions/intersection';
	import { useRect } from '$lib/lifecycle-functions/useRect';
	import { useWindowSize } from '$lib/lifecycle-functions/useWindowSize';
	import { useScroll } from '$lib/lifecycle-functions/useScroll';
	import { clamp, mapRange } from '$lib/utils/maths';
	import { dynamicImport } from '$lib/utils/dynamicImport';
	import Hero from '$lib/components/Hero.svelte';
	import About from '$lib/components/About.svelte';
	import Experience from '$lib/components/Experience.svelte';


	let hasScrolled = false;
	let visible = false;

	const [size] = useWindowSize();
	const [setZoomWrapperRectRef, zoomWrapperRect] = useRect();
	const [setWhyRectRef, whyRect] = useRect();
	const [setCardsRectRef, cardsRect] = useRect();
	const [setWhiteRectRef, whiteRect] = useRect();
	const [setFeaturesRectRef, featuresRect] = useRect();
	const [setInuseRectRef, inuseRect] = useRect();

	let zoomWrapperRef: HTMLElement;
	let whyRef: HTMLElement;
	let cardsRectRef: HTMLElement;
	let whiteRectRef: HTMLElement;
	let featuresRectRef: HTMLElement;
	let inuseRectRef: HTMLElement;

	$: if (Object.keys($homePageLoadedComponentsStore).length === 4) {
		setRectRefs();

		setTimeout(() => {
			updateThresholds();
		}, 800);
	}


	useScroll(({ scroll }) => {
		hasScrolled = scroll > 10;

		if (!zoomWrapperRef) return;

		const start = $zoomWrapperRect.top + $size.height * 0.5;
		const end = $zoomWrapperRect.top + $zoomWrapperRect.height - $size.height;

		const center = 0.6;
		const progress = clamp(0, mapRange(start, end, scroll, 0, 1), 1);
		const progress1 = clamp(0, mapRange(0, center, progress, 0, 1), 1);
		const progress2 = clamp(0, mapRange(center - 0.055, 1, progress, 0, 1), 1);

		const theme = progress2 === 1 ? 'light' : 'dark';
		if (theme !== $themeStore) {
			setThemeStore(theme);
		}

		zoomWrapperRef.style.setProperty('--progress1', String(progress1));
		zoomWrapperRef.style.setProperty('--progress2', String(progress2));

		if (progress === 1) {
			zoomWrapperRef.style.setProperty('background-color', 'currentColor');
		} else {
			zoomWrapperRef.style.removeProperty('background-color');
		}
	});

	function setRectRefs() {
		setZoomWrapperRectRef(zoomWrapperRef);
		setWhyRectRef(whyRef);
		setCardsRectRef(cardsRectRef);
		setWhiteRectRef(whiteRectRef);
		setFeaturesRectRef(featuresRectRef);
		setInuseRectRef(inuseRectRef);
	}

	function updateThresholds() {
		addThreshold({ id: 'top', value: 0 });

		const top1 = $whyRect.top - $size.height / 2;
		addThreshold({ id: 'why-start', value: top1 });
		addThreshold({
			id: 'why-end',
			value: top1 + $whyRect.height
		});

		const top2 = $cardsRect.top - $size.height / 2;
		addThreshold({ id: 'cards-start', value: top2 });
		addThreshold({ id: 'cards-end', value: top2 + $cardsRect.height });
		addThreshold({
			id: 'red-end',
			value: top2 + $cardsRect.height + $size.height
		});

		const top3 = $whiteRect.top - $size.height;
		addThreshold({ id: 'light-start', value: top3 });

		const top4 = $featuresRect.top;
		addThreshold({ id: 'features', value: top4 });

		// const top5 = $inuseRect.top;
		const top5 = inuseRectRef.getBoundingClientRect().top;
		addThreshold({ id: 'in-use', value: top5 });

		const top6 = $lenis?.limit;
		addThreshold({ id: 'end', value: top6! });
	}
</script>

<Hero></Hero>
<section>

<About />
<h2>EXPÉRIENCES</h2>
<div class="contenaireExperience" > <!-- opacityEffect -->
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
		<p>Gestion des appels téléphonique </p>
		<p>Gestion administrative de dossier client</p>
		<p>Formation et tutorat des nouveaux arrivant</p>
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
		<p>Création de certificats électronique</p>
		<p>Gestion des dossiers internes</p>
		<p>Gestion de la clientèle</p>
		<p>Ouverture et tri de courrier</p>
		</Experience>
	</div>
</div>


</section>


<style lang="scss"> 
	@import '../../src/lib/styles/global.scss';
	section{
		transform: translateY(-219vh);
		padding: 110px;
		padding-bottom: 0;
		padding-top: 0 ;
		width: 100vw;
		overflow-x: hidden;
		
	}
	.contenaireExperience{
		overflow-x: hidden;
	}

	.opacityEffect{
		opacity: 0;
	}
	h2{
		margin-bottom: 116px;
	}

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