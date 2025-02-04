<script lang="ts">
	import {onMount} from "svelte";

	let currentTheme = $state("light");

	onMount(() => {
		setDefaultScheme();
	});

	function setDefaultScheme() {
		const localStorageTheme = localStorage.getItem("theme");
		if (localStorageTheme !== null) {
			currentTheme = localStorageTheme;
			return;
		}

		const systemSettingDark = window.matchMedia("(prefers-color-scheme: dark)");
		if (systemSettingDark.matches) {
			currentTheme = "dark";
		}

		setTheme(currentTheme);
	}

	function toggleTheme() {
		currentTheme = currentTheme === "light" ? "dark" : "light";
		setTheme(currentTheme);
	}

	function setTheme(theme: string) {
		document.querySelector("html")?.setAttribute("data-theme", theme);
		localStorage.setItem("theme", theme);
	}
</script>

<header class="px-4 lg:px-8">
	<a href="/" class="font-medium">Slava Zakharov</a>
	<div>
		<nav><ul></ul></nav>
		<button type="button " onclick={toggleTheme}>
			<svg class="fill-current size-4" viewBox="0 0 500 500"
				><title>Change to {currentTheme} theme</title><circle
					cx="248.48"
					cy="252.55"
					r="97.03"
				></circle><rect height="112.39" width="27.9" x="234.53" y="17.45"
				></rect><rect height="112.39" width="27.9" x="234.53" y="375.25"
				></rect><rect
					height="112.39"
					transform="translate(679.92 -174.83) rotate(90)"
					width="27.9"
					x="413.42"
					y="196.35"
				></rect><rect
					height="112.39"
					transform="translate(322.12 182.97) rotate(90)"
					width="27.9"
					x="55.63"
					y="196.35"
				></rect><rect
					height="112.39"
					transform="translate(198.96 -228.23) rotate(45)"
					width="27.9"
					x="361.03"
					y="69.85"
				></rect><rect
					height="112.39"
					transform="translate(303.75 24.77) rotate(45)"
					width="27.9"
					x="108.03"
					y="322.85"
				></rect><rect
					height="112.39"
					transform="translate(908.15 381.93) rotate(135)"
					width="27.9"
					x="361.03"
					y="322.85"
				></rect><rect
					height="112.39"
					transform="translate(297.35 128.93) rotate(135)"
					width="27.9"
					x="108.03"
					y="69.85"
				></rect></svg
			>
		</button>
	</div>
</header>
