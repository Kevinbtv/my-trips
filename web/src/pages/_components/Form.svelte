<script lang="ts">
	import type { FormData } from './@types';

	export let formData: FormData,
		submitFunction: () => void,
		buttonName: string,
		feedBack = '';
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
<form
	on:submit|preventDefault={submitFunction}
	on:click={() => (feedBack = '')}
>
	<div class="places">
		<label>
			Local:
			<input type="text" bind:value={formData.local} required />
		</label>
		<label>
			País:
			<input type="text" bind:value={formData.country} required />
		</label>
	</div>
	<label>
		Descrição:
		<textarea bind:value={formData.description} required />
	</label>

	<button type="submit">{buttonName}</button>
</form>
{#if feedBack}
	<p class="feedback">Enviado com sucesso!</p>
{/if}

<style lang="scss">
	@import './theme/all';

	form {
		.places {
			display: flex;
			gap: 1rem;
		}

		label {
			display: block;
			margin-bottom: 0.625rem;
			width: 100%;

			input,
			textarea {
				border-radius: 0.3125rem;
				border: 0.0625rem solid my-trips-color(light-gray);
				box-sizing: border-box;
				font: inherit;
				margin: 0.5rem 0;
				padding: 0.625rem;
				width: 100%;
			}

			textarea {
				height: 12.5rem;
			}
		}

		button {
			background-color: my-trips-color(ocean-blue);
			border-radius: 0.3125rem;
			border: none;
			color: my-trips-color(pure-white);
			cursor: pointer;
			margin-right: 0.625rem;
			padding: 0.625rem 1.25rem;
			transition: background-color 0.3s;

			&:hover {
				background-color: my-trips-color(cerulean-blue);
			}
		}
	}

	.feedback {
		color: my-trips-color(forest-green-darker);
		font-weight: bold;
		margin-top: 0.625rem;
	}
</style>
