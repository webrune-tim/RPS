<script>
	export let checked = false;
	export let handleToggle;
</script>

<div>
	<input type="checkbox" {checked} on:click={handleToggle} id="switch" />
	<label for="switch">Toggle</label>
</div>

<style>
	div {
		margin: 1rem 0;
	}

	input[type='checkbox'] {
		height: 0;
		width: 0;
		visibility: hidden;
	}

	label {
		cursor: pointer;
		text-indent: -9999px;
		width: 100px;
		height: 50px;
		background: var(--bright-color);
		display: block;
		border-radius: 100px;
		position: relative;
	}

	label:after {
		content: '';
		position: absolute;
		top: 2.5px;
		left: 5px;
		width: 45px;
		height: 45px;
		background: var(--text-color);
		border-radius: 45px;
		transition: 0.3s;
	}

	input:checked + label:after {
		left: calc(100% - 5px);
		transform: translateX(-100%);
	}

	label:active:after {
		width: 65px;
	}

	@media (max-width: 600px) {
		label {
			width: 50px;
			height: 25px;
		}

		label:after {
			top: 1px;
			width: 22.5px;
			height: 22.5px;
			border-radius: 22.5px;
		}
		label:active:after {
			width: 32.4px;
		}
	}
</style>
