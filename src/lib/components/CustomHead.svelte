<script lang="ts">
	export let title = '';
	export let description = '';
	export let image = '';
	export let keywords: string[] = [];
</script>

<svelte:head>
	<!-- <meta httpEquiv="x-ua-compatible" content="ie=edge" />
	<meta httpEquiv="x-dns-prefetch-control" content="off" />
	<meta httpEquiv="Window-Target" content="_value" /> -->

	<title>{title}</title>

	<meta
		name="robots"
		content={process.env.NODE_ENV !== 'development' ? 'index,follow' : 'noindex,nofollow'}
	/>
	<meta
		name="googlebot"
		content={process.env.NODE_ENV !== 'development' ? 'index,follow' : 'noindex,nofollow'}
	/>

	<meta
		name="keywords"
		content={`${keywords && keywords.length ? keywords.join(',') : keywords}`}
	/>
	<meta name="author" content="Studio Freight" />
	<meta name="referrer" content="no-referrer" />
	<meta name="format-detection" content="telephone=no" />
	<meta name="geo.region" content="US" />
	<link rel="manifest" href="/site.webmanifest" />
	<link rel="manifest" href="/site.webmanifest" />
	<link rel="mask-icon" href="/safari-pinned-tab.svg" color="#721394" />
	<meta name="msapplication-TileColor" content="#000000" />
	<meta name="theme-color" content="#ffffff" />
	<link rel="icon" href="/favicon.ico" />
</svelte:head>

