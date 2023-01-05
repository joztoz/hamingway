<script>
	export let choosenStory
	export let animationEnded
	export let bookHasBeenRead
</script>

<style>
	h2 {
		color: #ff3e00;
		font-size: 2.5em;
		font-weight: 900;
		text-transform: uppercase;
		text-shadow: 3px 3px 0 #000;
		-webkit-text-stroke: 2px #710000;
		letter-spacing: -2px;

		position: absolute;
		margin-top: 0;
		left: 0;
		right: 0;
		margin-left: auto;
		margin-right: auto;
		top: 23vh;
	}

	h2 small {
		color: #d2c312;
		font-size: 0.65em;
	}

	h2 small::before {
		text-transform: lowercase;
		font-size: 0.75em;
	}

    @media (max-width: 640px) {
    
	h2 {
        text-shadow: 1px 1px 0 #000;
        letter-spacing: 1px;
		font-size: 1em;
        font-weight: 700;
        -webkit-text-stroke: 1px #710000;
	}
}
</style>

<h2
	class="animate__animated"
	class:animate__tada={animationEnded}
	class:animate__backOutDown={bookHasBeenRead}>

	<span>{choosenStory.title}</span>

	{#if choosenStory.page}
		<small>{choosenStory.page}</small>
	{/if}
</h2>