<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>
<script lang="ts">
	import Dataframe from "@gradio/dataframe";
	const value = {
		data: [
			["Shinji", 14, true],
			["Rei", 14, false],
			["Asuka", 14, true],
			["Misato", 29, true]
		],
		headers: ["Name", "Age", "Pilot"],
		metadata: null
	};
	const datatype = ["str", "number", "bool"];
	function handle_change(e: any) {
		console.log("changed", e.detail);
	}
	function handle_select(e: any) {
		console.log("selected", e.detail);
	}
	function handle_input(e: any) {
		console.log("input", e.detail);
	}
</script>
<div class="eva-theme">
	<h1 class="eva-title">Neon Genesis Evangelion Dataframe</h1>
	<Dataframe
		{value}
		{datatype}
		show_search="Search Pilots"
		show_row_numbers={true}
		show_copy_button={true}
		show_fullscreen_button={true}
		editable={true}
		label="Evangelion Pilots"
		show_label={true}
		on:change={handle_change}
		on:select={handle_select}
		on:input={handle_input}
	/>
</div>
<style>
	.eva-theme {
		min-height: 100vh;
		background: linear-gradient(135deg, #1a0033 0%, #2d0036 100%);
		color: #e5e7eb;
		font-family: 'Orbitron', 'Roboto Mono', 'Arial', sans-serif;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: flex-start;
		padding: 2rem;
	}
	.eva-title {
		font-size: 2.5rem;
		font-weight: 900;
		letter-spacing: 0.1em;
		color: #7c3aed;
		text-shadow: 0 0 10px #ff00cc, 0 0 20px #7c3aed;
		margin-bottom: 2rem;
		text-align: center;
	}
	.df-theme {
		--border-color-primary: #7c3aed;
		--radius-md: 10px;
		--background-fill-primary: #0b1020;
		--table-even-background-fill: #121936;
		--table-odd-background-fill: #0e1530;
		--body-text-color: #e5e7eb;
		--input-text-size: 16px;
		--focus-color: #ff00cc;
		--accent-color: #7c3aed;
	}
	:global(.df-theme) {
		font-family: 'Orbitron', 'Roboto Mono', 'Arial', sans-serif;
	}
	:global(.df-theme table) {
		box-shadow: 0 0 20px #7c3aed44;
		border-radius: var(--radius-md);
		border: 2px solid var(--border-color-primary);
		background: var(--background-fill-primary);
	}
	:global(.df-theme th), :global(.df-theme td) {
		color: var(--body-text-color);
		font-size: var(--input-text-size);
		border-color: var(--border-color-primary);
	}
	:global(.df-theme tr:nth-child(even)) {
		background: var(--table-even-background-fill);
	}
	:global(.df-theme tr:nth-child(odd)) {
		background: var(--table-odd-background-fill);
	}
	:global(.df-theme input:focus), :global(.df-theme button:focus) {
		outline: 2px solid var(--focus-color);
		box-shadow: 0 0 10px var(--focus-color);
	}
	:global(.df-theme button) {
		background: var(--accent-color);
		color: #fff;
		border-radius: 6px;
		border: none;
		padding: 0.5em 1em;
		box-shadow: 0 0 10px #ff00cc44;
		transition: background 0.2s;
	}
	:global(.df-theme button:hover) {
		background: #ff00cc;
	}
</style>
