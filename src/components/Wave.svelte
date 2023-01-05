<script>
export let where
export let animation
export let waving
</script>

<style>

.wave {
		width: 100vw;
		height: 40vh;
		position: absolute;
		bottom: 35px;
		right: 0;
		background: url('../assets/waves.png') bottom left repeat-x;
		background-size: 40%;
		animation-duration: 2s;
		animation-iteration-count: infinite;
	}
	.front {
		bottom: -15px;
		background-size: 30%;
	}
	.middle {
		bottom: 15px;
	}
	.bounce__big {
		animation-name: bounce__big;
		animation-timing-function: ease;
	}
	@keyframes bounce__big {
		0% {
			transform: translateY(0);
		}
		20% {
			transform: translateY(-10px);
		}
		50% {
			transform: translateY(0);
		}
		75% {
			transform: translateY(0);
		}
		100% {
			transform: translateY(0);
		}
	}
	.bounce__small {
		animation-name: bounce__small;
		animation-timing-function: ease;
	}
	@keyframes bounce__small {
		0% {
			transform: translateY(0);
		}
		20% {
			transform: translateY(0);
		}
		50% {
			transform: translateY(-5px);
		}
		75% {
			transform: translateY(0);
		}
		100% {
			transform: translateY(0);
		}
	}
	.bounce__tiny {
		animation-name: bounce__tiny;
		animation-timing-function: ease;
	}
	@keyframes bounce__tiny {
		0% {
			transform: translateY(0);
		}
		20% {
			transform: translateY(-3px);
		}
		50% {
			transform: translateY(0);
		}
		75% {
			transform: translateY(0);
		}
		100% {
			transform: translateY(0);
		}
	}

	@media (max-width: 640px) {
		
.wave {
		bottom: 40px;
		right: 0;
		background: url('../assets/waves.png') bottom left repeat-x;
		background-size: 40%;
		animation-duration: 2s;
		animation-iteration-count: infinite;
	}
	.front {
		bottom: -10px;
	}
	.middle {
		bottom: 20px;
	}
	}

</style>

{#if waving}
    <div class="wave {where} bounce__{animation}"></div>
{:else}
    <div class="wave {where}"></div>
{/if}

