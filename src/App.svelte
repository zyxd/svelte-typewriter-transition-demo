<main>
	<h1>
		<a href="https://github.com/zyxd/svelte-typewriter-transition">
			svelte-typewriter-transition
		</a>
	</h1>
	{#if text_1}
		<h2
			in:typewriter={{speed: 100, separator: '\n'}}
			out:fade
			on:introend={() => text_2 = true}
			on:outroend={() => text_1 = true}
		>
			Hi
			Hey
			Hello world
			Hello!
			Hello. My name is
			Hello!
		</h2>
	{/if}
	{#if text_2}
		<h3
			in:typewriter={{speed: 80, separator: '\n'}}
			out:fade
			on:introend={() => text_3 = true}
		>
			Svelte iis
			Svelte is a radical now approach
			Svelte is a radical new approach to building usr inte
			Svelte is a radical new approach to building user interfaces.
		</h3>
	{/if}
	{#if text_3}
		<p
			in:typewriter={{speed: 50 }}
			out:fade
			on:introend={() => text_4 = true}
		>
			Svelte compiles your code to tiny, framework-less 
			vanilla JS — your app starts fast and stays fast.
		</p>
	{/if}
	{#if text_4}
		<i
			in:typewriter={{speed: 100}}
			out:typewriter={{speed: 30}}
			on:introend={() => setTimeout(() => text_4 = false, 1000)}
			on:outroend={() => setTimeout(reset, 2000)}
		>
			Once entered, this text should be quickly erased.
		</i>
	{/if}
</main>

<script>
	import { onMount, tick } from 'svelte'
	import { fade } from 'svelte/transition'
	import typewriter from 'svelte-typewriter-transition'
	
	let text_1 = false
	let text_2 = false
	let text_3 = false
	let text_4 = false
	
	const reset = async () => {
		text_1 = false
		text_2 = false
		text_3 = false
		text_4 = false
	}
	
	onMount(() => text_1 = true)
</script>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 2rem;
		font-weight: 100;
	}

	h2 {
		font-size: 1.5rem;
	}

	h3 {
		font-size: 1.0rem;
	}

	a {
		color: inherit;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>