<script lang="ts">
	import "$lib/css/app.css";
	import {onMount} from "svelte";
	import type {Snippet} from "svelte";
	import Banner from "$lib/components/Banner.svelte";

	let {children}: {children: Snippet} = $props();
</script>

<Banner msg="Stop war in Ukraine!" />
<main class="grid-rows-main grid min-h-[calc(100dvh-2rem)]">
	<Header />

	<div class='min-h-[60dvh] lg:min-h-full'>
		{@render children()}
	</div>

	<footer>footer</footer>
</main>
