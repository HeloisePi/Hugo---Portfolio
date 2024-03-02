<script lang="ts">
	import { onMount, type ComponentType } from 'svelte';
	import Lenis from '@studio-freight/lenis';
	import { gsap } from 'gsap';
	import {CustomEase} from "gsap/CustomEase";
	import { ScrollTrigger } from 'gsap/dist/ScrollTrigger';
	import cn from 'clsx';

	import { browser } from '$app/environment';
	import { page } from '$app/stores';
	import { lenisStore as lenis, setLenisStore } from '$lib/stores/lenis';
	import { themeStore } from '$lib/stores/theme';
	import { useScroll } from '$lib/lifecycle-functions/useScroll';
	import { useFrame } from '$lib/lifecycle-functions/useFrame';
	import { raf } from '$lib/utils/tempus';

	import CustomHead from '$lib/components/CustomHead.svelte';
	
	import Footer from '$lib/components/Footer.svelte';

	import '$lib/styles/global.scss';
	import Header from '$lib/components/Header.svelte';
	import HeaderMobile from '$lib/components/utilities/HeaderMobile.svelte';

	let className = '';

	export { className as class };

	if (browser) {
		gsap.registerPlugin(ScrollTrigger);

		// Merge rafs
		gsap.ticker.remove(gsap.updateRoot);
		raf.add((time) => {
			gsap.updateRoot(time! / 1000);
		}, 0);
	}

	let Cursor: ComponentType;
	let hash = '';

	useScroll(ScrollTrigger.update);

	ScrollTrigger.defaults({ markers: process.env.NODE_ENV === 'development' });

	// $: if (browser && $lenis) {
	// 	ScrollTrigger.refresh();
	// }

	$: if (browser && $lenis) {
		ScrollTrigger.refresh();
		$lenis.start();
		// document.documentElement.style.removeProperty('overflow');
	}
	// else if (browser) {
	// 	$lenis?.stop();
	// 	document.documentElement.style.setProperty('overflow', 'hidden');
	// }

	$: if (browser && $lenis && hash) {
		const target = document.querySelector(hash);
		$lenis.scrollTo(target, { offset: 0 });
	}

	onMount(async () => {
		Cursor = (await import('../lib/components/Cursor.svelte')).default;

		window.history.scrollRestoration = 'manual';
		window.scrollTo(0, 0);

		const lenisInstance = new Lenis();
		setLenisStore(lenisInstance);

		function onLinkClick(e: MouseEvent) {
			e.preventDefault();

			const node = e.currentTarget;
			const nodeHash = (node as HTMLLinkElement).href.split('#').pop();

			hash = '#' + nodeHash;

			setTimeout(() => {
				window.location.hash = hash;
			}, 0);
		}

		const internalLinks: Element[] = [...document.querySelectorAll('[href]')].filter((node) =>
			(node as HTMLLinkElement).href.includes($page.url.pathname + '#')
		);

		internalLinks.forEach((node) => {
			(node as HTMLLinkElement).addEventListener('click', onLinkClick, false);
		});

		return () => {
			internalLinks.forEach((node) => {
				(node as HTMLLinkElement).removeEventListener('click', onLinkClick, false);
			});

			$lenis?.destroy();
			// setLenisStore(null);
		};
	});

	useFrame((time) => {
		$lenis?.raf(time);
	});



	// -----------------------------------------------------


	onMount(() => {
    gsap.registerPlugin(ScrollTrigger);

    const elements = document.querySelectorAll('.opacityEffect');

    elements.forEach((element) => {
        gsap.fromTo(
            element,
            {
                opacity: 0,
            },
            {
                opacity: 1,
                duration: 0.25, // Durée de l'animation en secondes
                scrollTrigger: {
                    trigger: element,
                    start: 'top 99%',
                    end: 'bottom top',
					once: true,
					markers: false,
                    scrub: true, // Effet de "frottement" pendant le défilement
					
                },
            }
        );
    });
});
</script>

<!-- <RealViewport /> -->
<CustomHead title="Portfolio – Hugo MENSAH" />
<div class={cn(`theme-${$themeStore}`, 'layout', className)}>
	<!-- <PageTransition /> -->
	<div class="headerdesktop">
		<Header />
	</div>
	<div class="headerdmobile">
		<HeaderMobile />
	</div>
	
	<svelte:component this={Cursor} />

	<main class="main"><slot /></main>
	<Footer/>
</div>

<style lang="scss">
	@import '../lib/styles/_functions';


	.headerdesktop {
        display: block;
      }
      .headerdmobile {
        display: none;
        width: 100vw;
      }
      @media screen and (max-width: 1200px) {
      .headerdesktop {
        display: none;
      }
      .headerdmobile {
        display: block;
        width: 100vw;
      }
	
	}

	.layout {
		
		display: flex;
		flex-direction: column;
		min-height: 100vh;

		.main {
			flex-grow: 1;
		}
	}


	.opacityEffect{
		opacity: 0;
	}
	h2{
		margin-bottom: 116px;
	}
</style>
