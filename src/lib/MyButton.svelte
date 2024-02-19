<script>
	export let size = 'small'
	export let shadow = false
</script>

<button on:click
	class:size-lg={size === 'large'} 
	class:size-sm={size === 'small'} 
	class:shadow>
	{#if $$slots.leftContent}
		<div class="left-content">
			<slot name="leftContent"/>
		</div>
	{/if}
	<slot />
</button>

<style lang="scss">
	button {
		display: flex;
		align-items: center;
		border: none;
		background-color: #ff3e00;
		color: #ffffff;		
		font-weight: bold;
		border-radius: 5px;
		cursor: pointer;
		.left-content {
			margin-right: 10px;
		}
		&:hover {
			background-color: #ff5e00;
		}
		&:active {
			background-color: #008000;
		}
		&.size-sm {
			padding: 15px 20px;
		}
		&.size-lg {
			padding: 20px 25px;
		}
		&.shadow {
			box-shadow: 0 0 10px rgb(241, 206, 206);
		}
	}
</style>