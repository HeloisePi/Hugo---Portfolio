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
	import AllExperience from '$lib/components/AllExperience.svelte';
	import AllPreviewProject from '$lib/components/AllPreviewProject.svelte';
	import CarouselDrawing from '$lib/components/CarouselDrawing.svelte';
	import Contact from '$lib/components/Contact.svelte';


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

<div class="contenaireStain">
	<img class="stain stain1" src="/stain/stain1.svg" alt="tâche">
	<img class="stain stain2" src="/stain/stain2.svg" alt="tâche">
	<img class="stain stain3" src="/stain/stain3.svg" alt="tâche"> 
</div>
<section>
<Hero
title="Portfolio"
title2="Hugo MENSAH"></Hero>


<About />
<div class="relative">
<AllExperience />
<div class="contenaireStain secondContenaireStain">
	<img class="stain stain1" src="/stain/stain1.svg" alt="tâche">
	<img class="stain stain2" src="/stain/stain2.svg" alt="tâche">
	<img class="stain stain3" src="/stain/stain3.svg" alt="tâche"> 
</div>
</div>	

<AllPreviewProject>
</AllPreviewProject>

<div class="relative">
<div class="secondContenaireStain contenaireStain">
	<img class="stain stain1" src="/stain/stain1.svg" alt="tâche">
	<img class="stain stain2" src="/stain/stain2.svg" alt="tâche">
	<img class="stain stain3" src="/stain/stain3.svg" alt="tâche"> 
</div>
<CarouselDrawing />
</div>
<Contact />
</section>


<style lang="scss"> 
	@import '../../src/lib/styles/global.scss';
	section{
		padding: 110px;
		padding-top: 0 ;
		width: 100vw;
		overflow-x: hidden;
		display: flex;
		flex-direction: column;
		padding-bottom: 148px;
		
	}
	@media screen and (max-width: 900px) {
        section{
			padding: 30px;
			padding-bottom: 148px;
		}
		.relative .secondContenaireStain{
			transform: translate(-30px, -70vh);
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
		z-index: 0;
	}

	.secondContenaireStain{
		z-index: 0;
		padding: 100vh;
		padding-left: 0;
		padding-right: 0;
		transform: translate(-110px, -70vh);
		padding-bottom: 190vh;
	}

	.contenaireExperience{
		overflow-x: hidden;
	}


	// 						Stain


	.relative{
		position: relative;
		width: 100%;
		height: fit-content;
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