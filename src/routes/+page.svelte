<script>
	// Creamos varias flores que caerán
	let flores = Array.from({ length: 50 }, (_, i) => ({
		id: i,
		left: Math.random() * 100, // posición horizontal
		delay: Math.random() * 5, // inicio aleatorio
		duration: 8 + Math.random() * 5 // velocidad distinta
	}));
</script>

<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap" rel="stylesheet" />

<!-- Fondo cubierto -->
<div class="fondo"></div>

<!-- Mensaje romántico -->
<div class="mensaje">
	<h1>Para ti, mi amor</h1>
	<p>Un jardín eterno de flores amarillas solo para ti 💛</p>
</div>

<!-- Flores cayendo -->
{#each flores as flor}
	<img
		src="/flor.png"
		alt="flor amarilla"
		class="flor"
		style="
      left: {flor.left}%;
      animation-duration: {flor.duration}s;
      animation-delay: {flor.delay}s;
    "
	/>
{/each}

<style>
	body {
		margin: 0;
		overflow: hidden;
		font-family: 'Comic Sans MS', cursive, sans-serif;
	}

	.fondo {
		position: fixed;
		width: 100%;
		height: 100%;
		background: url('/fondo.png') no-repeat center center;
		background-size: cover; /* ajusta el tamaño de las flores del fondo */
		background-repeat: repeat;
		z-index: 0;
	}

	.mensaje {
		position: absolute;
		top: 40%;
		left: 50%;
		transform: translate(-50%, -50%);
		text-align: center;
		color: #000000;
		z-index: 10;
	}

	.mensaje h1 {
		font-family: 'Great Vibes', cursive;
		font-size: 4rem;
		font-weight: normal;
		text-shadow: 3px 3px 8px #00000055;
		margin: 0;
	}

	.mensaje p {
		font-family: 'Great Vibes', cursive;
		font-size: 2.2rem;
		text-shadow: 2px 2px 6px #00000044;
		margin-top: 1rem;
	}

	.flor {
		position: absolute;
		top: -10vh;
		width: 60px;
		height: 60px;
		animation-name: caer;
		animation-timing-function: linear;
		animation-iteration-count: infinite;
		z-index: 5;
	}

	@keyframes caer {
		from {
			transform: translateY(-10vh) rotate(0deg);
		}
		to {
			transform: translateY(110vh) rotate(360deg);
		}
	}
</style>
