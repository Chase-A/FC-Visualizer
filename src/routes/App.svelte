<script>
	let ftemp = $state(70);
	let minTemp = -50;
	let maxTemp = 134;

	function getIndex() {
		if (ftemp < -3) return 0;
		if (ftemp < 15) return 1;
		if (ftemp < 32) return 2;
		if (ftemp < 50) return 3;
		if (ftemp < 65) return 4;
		if (ftemp < 72) return 5;
		if (ftemp < 90) return 6;
		if (ftemp < 110) return 7;
		return 8;
  	}

	let descriptions = [
		"A cold day on the summit of Mt. Everest, Nepal",
		"So cold that it's recommended to stay inside",
		"Good conditions for skiing at your favorite mountain",
		"A cold rainy day, best to stay inside",
		"Cool and crisp, ideal weather for playing sports",
		"An average office's room temperature setting",
		"A warm day, perfect for enjoying the beach",
		"A heat wave, it's recommended to stay inside",
		"A hot day in Death Valley, California, USA"
	]

	let alt_texts = [
		"the peak of Mount Everest",
		"a group of people bundled up in scarves and heavy jackets",
		"skiers skiing down from a chairlift",
		"people standing on a city sidewalk holding umbrellas in the rain",
		"two soccer players chasing down a soccer ball",
		"a well lit modern office",
		"a wide angle shot of a beach on a clear summer day and the surrounding town",
		"four people sheltering themselves from the sun with a large sheet",
		"the valleys of Death Valley"
	]

	let images = [
		"./everest.jpg",
		"./cold.jpg",
		"./ski.jpg",
		"./rain.jpg",
		"./footy.jpg",
		"./office.jpg",
		"./beach.jpg",
		"./hot.jpg",
		"./death_valley.jpg"
	]

</script>

<div class="body">
	<div class="app-container">
		<img class="photo" src={images[getIndex()]} alt={alt_texts[getIndex()]}>
		<div class="bottom-container">
			<p class="img-description">{descriptions[getIndex()]}</p>	
			<div class="text-container">
				<p class="celcius">{Math.round((ftemp -32)* (5/9))}<span class="degrees">&deg;C</span></p>
				<p>{ftemp}<span class="degrees">&deg;F</span></p>
			</div>
			<input type="range" min={minTemp} max={maxTemp} bind:value={ftemp} />
		</div>
	</div>
</div>

<style>
	
	@import url('https://fonts.googleapis.com/css2?family=Reddit+Mono:wght@200..900&display=swap');

	:global(html){
		height: 100% !important;
	}
	:global(body){
		margin: 0;
		height: 100%;
	}
	.app-container {
		font-family: "Reddit Mono", monospace;
	}
	.bottom-container {
		display: flex;
		flex-direction: column;
		align-items: center;
		place-content: center;
		justify-content: space-evenly;
	}
	p {
		font-family: "Reddit Mono", monospace;
		font-size: 24px;
	}
	.text-container{
		display: flex;
		justify-content: space-between;
		margin: 0 auto;
		width: 70%;
		max-width: 250px;

	}
	.text-container p {
		font-family: "Reddit Mono", monospace;
		font-size: 64px;
		margin: 0;
		margin-bottom: 30px;
	}
	.text-container p .degrees {
		font-size: 24px;
		font-weight: 600px;
		vertical-align: top;
		position: relative;
		top: 12px;
	}
	.photo{
		width: 100%;
		/* max-width: 500px; */
		margin: 0 auto;
		height: auto;
		animation: fadeIn 100ms linear forwards;
	}
	.img-description {
		font-size: 20px;
		text-align: center;
		max-width: 400px;
		margin: 20px auto;
	}
	input {
		width: 90%;
		accent-color: #999;
	}
	@keyframes fadeIn {
		0% {
			opacity: 0;
		}
		100% {
			opacity: 1;
		}
	}

	@media(min-width: 800px){
		:global(body){
			height: 100%;
		}
		.body {
			display: flex;
			width: 100%;
			height: 100%;
			justify-content: center;
			align-items: center;
		}
		.app-container {
			display: flex;
			flex-direction: row;
			align-items: center;
			max-width: 1280px;
		}

		.photo {
			width: 50%;
			margin: 0;
		}
		.bottom-container {
			width: 50%;
			justify-content: space-between;
			height: 300px;
		}
		.text-container p {
			margin-bottom: 0;
		}
		.img-description {
			order: 2;
			margin: 0;
		}
		.text-container {
			order: 1
		}
		input {
			order: 3;
			width: 80%;
			margin-top: 20px;
		}
	}
</style>